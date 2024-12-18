**What is the Two-Phase Commit Protocol?**

It is a protocol to ensure atomicity in a distributed system. It consists of Two Phases.
  - Prepare Phase: A central coordinator sends out a "Prepare" message to all the nodes to check if all the nodes are ready to commit the transaction. Each node has to respond with "OK".
  - Commit Phase: If the coordinator receives an "OK" message from all the nodes, it sends out a "Commit" message to all the nodes asking them to commit the transaction, else sends out       an "ABORT" message to roll back.


------------------------------------------
