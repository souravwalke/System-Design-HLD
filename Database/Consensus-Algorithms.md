**What is the Two-Phase Commit Protocol?**

It is a protocol to ensure atomicity in a distributed system. It consists of Two Phases.

- Prepare Phase: A central coordinator sends out a "Prepare" message to all the nodes to check if all the nodes are ready to commit the transaction. Each node has to respond with "OK".
- Commit Phase: If the coordinator receives an "OK" message from all the nodes, it sends out a "Commit" message to all the nodes asking them to commit the transaction, else sends out  an "ABORT" message to roll back.

Although it is a good protocol to achieve consensus, it is slow due to the two phases involved and also is not fault-tolerant with a single point of failure.

------------------------------------------------------------------------------------------------------------------------------
**What is Raft and how does it work?**

Raft is a consensus algorithm that is used in distributed systems to achieve consistency or a single state. It is simple and fault-tolerant.

  1. When the leader receives a write request from the client, it first appends the write entry to its local log. Write is not committed it's just proposed.
  2. The leader replicates the log entry to all follower nodes by sending them an **"AppendEntries"** request.
  3. Each follower appends the log entry to its local log and sends an acknowledgment.
  4. Once the leader receives acknowledgments from a **majority (quorum)** of followers, it considers the write safe to commit.
  5. The leader marks the write as committed in its log and applies the change to its database state.
  6. The leader sends a **commit notification** to the followers, instructing them to also apply the write to their local databases.
  7. Upon receiving the commit notification, the followers mark the entry as committed and apply it to their database state.
  8. Finally, the leader acknowledges the success of the operation to the client.

**What if the leader fails in Raft?**

- The leader periodically sends out **heartbeat messages (or AppendEntries RPCs)** to all of its follower nodes.
- These heartbeats signal that the leader is still alive and functioning. It's a way of keeping followers informed and **preventing unnecessary elections**.
- Each follower has a **randomized election timeout**.
- If a follower doesn't hear from the leader (via heartbeats) within its timeout period, it assumes the leader has failed or is unreachable.
- The follower that first spots the failure transitions to a candidate state.
- The candidate increments its term (a logical clock indicating the current election period).
- The candidate starts an **election** by sending a **RequestVote RPC** to all other nodes, asking them to vote for it as the new leader.
- The **RequestVote RPC** request consists of the candidate's current term number and the local log state.
- The followers compare the term number and the log with their term number and local log. If the term number is higher and the log is up-to-date then they vote for the candidate.
- If a candidate node receives a majority of votes, it becomes the new leader and starts sending heartbeats to the followers.
- The new leader can then continue processing writes and keeping the logs synchronized.

------------------------------------------------------------------------------------------------------------------------------
