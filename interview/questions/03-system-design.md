# System Design Questions

System design interviews evaluate your ability to architect large-scale software systems. They are standard for mid-level (L4) and senior (L5+) roles and increasingly appear in modified form for junior roles. The format is typically 45-60 minutes of open-ended discussion.

## The Interview Format

A system design interview is a conversation, not a coding exercise. You drive the discussion while the interviewer guides, challenges, and probes. There is no single correct answer. The interviewer evaluates how you think through ambiguity, make tradeoffs, and communicate complex ideas.

Typical time breakdown:
- 5 minutes: problem statement and initial questions
- 5-10 minutes: requirements clarification and estimation
- 15-20 minutes: high-level design
- 15-20 minutes: detailed component design and deep dives
- 5 minutes: wrap-up, extensions, monitoring

## The Framework

I found that candidates who follow a consistent framework perform significantly better than those who improvise. Here is the framework I recommend.

Step 1: Requirements clarification (5-10 minutes)

Functional requirements: what should the system do? List the core use cases. For a URL shortener: create short URL, redirect to original URL, custom aliases, analytics.

Non-functional requirements: what qualities must the system have? Availability, consistency, latency targets, throughput, durability. Ask the interviewer: how many users? How many requests per second? What is the read-to-write ratio?

Constraints: what is out of scope? Clarifying what you are NOT building is as important as clarifying what you are.

Step 2: Back-of-envelope estimation (3-5 minutes)

Estimate traffic, storage, bandwidth, and memory requirements. This shows you can reason about scale.

Example for a URL shortener with 500 million URLs:
- 500M URLs * 500 bytes per record = 250 GB storage
- 100:1 read-to-write ratio, 1000 writes/sec = 100K reads/sec
- Daily new URLs: 1000 * 86400 = ~86M new URLs/day

Do not spend too long here. Round aggressively. The point is to establish order of magnitude, not precision.

Step 3: High-level design (10-15 minutes)

Draw the major components and how they interact. Start with the client, load balancer, application servers, database, and cache. Add components as needed: message queues, CDN, object storage, search index.

Keep it simple initially. Three to five boxes connected by arrows. The interviewer will ask you to go deeper on specific components.

Step 4: Detailed component design (15-20 minutes)

This is where the interviewer probes. Common deep-dive topics:
- Database schema and choice (SQL vs NoSQL, sharding strategy)
- Caching layer (what to cache, invalidation strategy, cache-aside vs write-through)
- Data partitioning (hash-based, range-based, consistent hashing)
- Replication and consistency model
- API design (REST endpoints, request/response format)

Step 5: Scalability and tradeoffs (5-10 minutes)

Discuss how the system handles growth. Where are the bottlenecks? How do you scale each component? What tradeoffs did you make (CAP theorem, latency vs consistency, cost vs performance)?

Step 6: Monitoring and error handling (2-5 minutes)

What metrics would you track? How do you detect and handle failures? What alerting would you set up? This demonstrates production-readiness thinking.

## What Interviewers Evaluate

I found consistent evaluation criteria across sources:

Requirements gathering. Did you ask the right questions? Did you scope the problem appropriately? Candidates who immediately start drawing diagrams without understanding the problem score poorly.

Architecture decisions. Are your choices reasonable for the scale and requirements? Can you justify why you chose SQL over NoSQL, or why you added a cache layer?

Tradeoff articulation. Can you explain what you gain and lose with each decision? "I chose eventual consistency because strong consistency would require coordination across data centers, adding 50-100ms latency per write" is better than "I chose eventual consistency."

Knowledge breadth. Do you know about the building blocks? Load balancers, databases, caches, message queues, CDNs, object storage, search engines. You do not need to be an expert in all of them, but you should know when to use each.

Communication. Can you explain your design clearly? Do you use the whiteboard effectively? Can you respond to challenges without getting defensive?

## Seniority Expectations

Junior (L3): rarely asked system design. When it appears, it is simplified. Design a simple API, a basic CRUD application. No expectation of distributed systems knowledge.

Mid-level (L4): expected to design a medium-complexity system. Should know caching, database choices, basic horizontal scaling. May struggle with data partitioning details, and that is acceptable.

Senior (L5): expected to drive the entire discussion with minimal guidance. Should handle partitioning, replication, consistency models, failure scenarios. Expected to proactively address bottlenecks.

Staff+ (L6+): expected to discuss cross-system interactions, organizational considerations, multi-region architecture, cost optimization, and technology evaluation frameworks. Should identify constraints the interviewer did not mention.

## Questions by Category

Web-Scale Systems

Design a URL shortener
Core: short URL generation (base62 encoding or hash), redirect service, analytics tracking.
Key decisions: how to generate unique short codes (counter-based vs hash-based), how to handle collisions, where to store mappings (SQL for durability vs Redis for speed), read-heavy optimization.
Scale considerations: 100K+ redirects per second, caching hot URLs, CDN for global latency, database sharding by short code prefix.

Design a Twitter/X feed
Core: tweet creation, fan-out (push vs pull), timeline generation, following/follower graph.
Key decisions: fan-out on write (pre-compute timelines) vs fan-out on read (compute at request time). Hybrid approach for celebrities. How to handle real-time updates (WebSocket vs polling).
Scale: 500M+ users, timeline generation under 200ms, write amplification from fan-out.

Design Instagram
Core: photo upload, feed generation, like/comment system, search and discovery.
Key decisions: object storage for images (S3-compatible), CDN for delivery, thumbnail generation pipeline, feed ranking algorithm. Separate read and write paths.
Scale: image storage (petabytes), CDN edge caching, async processing for image transformations.

Storage Systems

Design a distributed cache (like Redis cluster)
Core: in-memory key-value storage, expiration policies, data partitioning.
Key decisions: consistent hashing for data distribution, replication for availability, eviction policies (LRU, LFU), persistence options (snapshot vs append-only log).
Deep dive: how to handle cache stampede, hot keys, cluster rebalancing during node failures.

Design a key-value store
Core: put and get operations, durability, replication.
Key decisions: LSM tree vs B-tree for storage engine, write-ahead log for durability, quorum reads/writes for consistency, gossip protocol for cluster membership.
Deep dive: compaction strategies, read amplification vs write amplification, Bloom filters for read optimization.

Messaging Systems

Design a chat system (like WhatsApp/Slack)
Core: 1-to-1 messaging, group messaging, online status, message delivery guarantees.
Key decisions: WebSocket for real-time delivery, message ordering (vector clocks or server-assigned timestamps), offline message queue, end-to-end encryption architecture.
Scale: millions of concurrent WebSocket connections, message fanout for group chats, media message handling.

Design a notification service
Core: multi-channel delivery (push, email, SMS, in-app), user preferences, rate limiting.
Key decisions: message queue for async processing, priority levels, deduplication, retry logic with exponential backoff, template management.
Scale: billions of notifications per day, handling burst traffic (marketing campaigns), provider failover.

Streaming Systems

Design a video streaming platform (like YouTube/Netflix)
Core: video upload, transcoding, adaptive streaming, content delivery.
Key decisions: transcoding pipeline (multiple resolutions, codecs), CDN with edge caching, adaptive bitrate streaming (HLS/DASH), recommendation engine.
Scale: petabytes of video storage, millions of concurrent streams, global CDN network.

Design a real-time analytics system
Core: event ingestion, aggregation, querying, dashboarding.
Key decisions: event streaming (Kafka), stream processing (Flink/Spark Streaming), pre-aggregated vs raw storage, approximate counting (HyperLogLog).
Scale: millions of events per second, sub-minute query latency, long-term storage and retention.

Search Systems

Design a search engine
Core: crawling, indexing, ranking, serving.
Key decisions: inverted index structure, ranking algorithm (TF-IDF, BM25, learned ranking), index partitioning (by document vs by term), query understanding (spell correction, synonyms, semantic search).
Scale: billions of documents, sub-second query latency, incremental index updates.

Design an autocomplete system
Core: prefix matching, ranking by popularity, personalization.
Key decisions: trie data structure vs prefix-based search, pre-computed top suggestions, real-time vs batch ranking updates, multi-language support.
Scale: sub-50ms latency requirement, millions of QPS, graceful degradation under load.

## How to Prepare

Study the building blocks. Before tackling full system designs, make sure you understand: load balancers, application servers, databases (SQL and NoSQL), caching (Redis, Memcached), message queues (Kafka, RabbitMQ), CDNs, object storage, search engines (Elasticsearch), and monitoring tools.

Practice 2-3 designs per week. Use a timer. Explain your design out loud, even if you are alone. Record yourself if possible and listen back.

Read engineering blogs. Companies like Netflix, Uber, Airbnb, Meta, and Google publish detailed architecture posts. These give you real-world examples of design decisions and their consequences.

Watch mock system design interviews. YouTube has several channels with realistic mock interviews. Observe how experienced candidates structure their answers and handle pushback.

## Common Mistakes

Starting to draw without understanding requirements. Always clarify first.

Going too deep on one component while ignoring others. Balance breadth and depth. Cover the full system at a high level before diving deep.

Not discussing tradeoffs. Every decision has consequences. Saying "I would use MongoDB" without explaining why (and what you lose compared to PostgreSQL) is insufficient.

Ignoring failure scenarios. What happens when a server goes down? What happens when the database is full? What happens during a network partition? Production systems fail, and your design should account for it.

Memorizing designs instead of understanding principles. If you memorize a URL shortener design but cannot adapt when the interviewer changes the requirements, you will struggle. Focus on principles (partitioning, replication, caching, async processing) that apply across designs.
