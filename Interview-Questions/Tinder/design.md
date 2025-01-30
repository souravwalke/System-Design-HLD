**Design Tinder - Online Dating Application**

Tinder is a mobile application where two people can find love.

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Requirement**

**Functional Requirement**

1. User should be able to provide their preferences. (minAge, maxAge, minRadius, gender...)
2. The user should be able to see a stack of profiles
   - based on location
   - based on entered preferences
3. User should be able to swipe (left/ right)
4. Users should be notified when they get matched

Potential Questions:
1. Should I design the profile creation part as well?
2. What is the scale of the system?
3. Can users see the same profile again if they swipe left?

**Non-Functional Requirements**

1. Prefer Consistency >> Availability in case of swipes and Availability >> Consistency in most other cases. (CAP Theorem)
2. Should support a scale of 100M+ monthly active users (MAUs).
3. Low latency profile feed generation (<300 ms) - Near real-time

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Basic Capacity Estimation**

1. **QPS Estimation**

   100M MAU --> 10% Of this will be DAU so 10M DAU.
   Avg Person swipes 100 profiles in the stack

   10M * 100 -> 1B swipes/day

   100M swipes/day --> 1000/86400 == 12K QPS (Approx)

   By doing this calculation we can conclude that the application has a high write workload and should support high write throughput.

2. **Storage Estimation**

   DAU -> 10M 
   Swipe Data Storage per swipe (uncompressed): 25 bytes
   Total swipes/day = 10M users × 100 swipes = 1B swipes/day
   Storage per day = 1B × 25 bytes = 25GB/day

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Core Entities**

These are the actors/objects that are going to be forming the foundation of our data model. These usually align with the nouns in the functional requirements. Although I will not go in-depth in designing the data model just yet. I will just identify these entities for now.

1. Profile
2. Swipes
3. Matches

---------------------------------------------------------------------------------------------------------------------------------------------------------

**API Design**

APIs form an agreement between the client and the server and establish the kind of request and response that will be generated. These could evolve as we delve deeper into the design. Refer to the functional requirements and satisfy these requirements 

1) User should be able to provide their preferences.

   POST /v1/users {   -> Response: 200 Success Code
     minAge,
     maxAge,
     radius,
     gender...
   }

2) User should be able to see a stack of profiles

   GET /feed?lat={}&long={}&distance={} -> -> Response: Users[]

3) User should be able to swipe

   POST /v1/swipe {   -> Response ?Match / 200   (Match is returned when two people swipe right on each other)
     decision
   }

4) It is not a user-facing API so there won't be any specific API for this.
   
---------------------------------------------------------------------------------------------------------------------------------------------------------

**High-Level Design**

1) We will have a client which is majorly a mobile device.
   
2) We will define a load balancer and an API gateway. I am using the API gateway as I will be adopting a microservices architecture for my design. The API gateway will handle the          routing, authorization, and rate limiting.

3) Let's start with the implementation of the first API (setting user preferences). We will define a "Profile Service" and route out requests to this service. The preferences data and    basic profile data will be persisted in our database. Here the choice of database doesn't matter (Can be PostgreSQL/DynamoDB/MongoDB) since profile data has limited scalability 
   and doesn't have too many complex schema relationships.

4) Next we will need to focus on generating the feed for swiping. We will not have a separate service for this. We can call the same "Profile Service". Then we can run a query on the     profiles DB to get the current user's preferences. We can then run another query using these preferences as a parameter to get all the profiles that match the requirement.

5) Although the query we would be running is very inefficient. We can optimize this part in the later design. Searching by location in particular, even with basic indexing, would be 
   incredibly slow. 

6) Once users have their "stack" of profiles they're ready to find love!

7) The user can swipe right or left and our system needs to capture this swipe to determine a match. We will define a "Swipe Service" that will handle the swipes. We will also define     a swipe database that stores swipe data for users.

8) The swipe DB will store the user ID of the person who swiped, the opposite person's user ID and the decision, and certain other metadata. As per our initial estimations, we had        seen that the workload would be skewed towards more writes. Therefore we would need a DB that is optimized for writes (Cassandra).

10) Basically when a user swipes, the swipe service updates the Swipe Database with the swipe data. It also checks if there is an inverse swipe in the Swipe Database and, if so,           returns a match to the client.

11) A push notification will be triggered to the user who had swiped first. We can use Apple push notifications or Android-specific notifications.

---------------------------------------------------------------------------------------------------------------------------------------------------------

**Deep Dives**

1) How can you make swipes consistent?

   The idea of making swipes consistent comes from a scenario when two people swipe right on each other at the exact same time. Based on our current design we could miss capturing a      match as each of the requests fails to see the other's decision. If capturing this "Match" is missed, the user won't be notified at all.

   One solution for this would be to not have any consistency for swipes. What I mean is, that we can capture the swipes as we did previously and store in the DB. We could then run a     cron job periodically to check if there are any matches and then send a push notification.

   The next solution could be to poll the database regularly to see if there are any matches. It however introduces latency.

   
   
