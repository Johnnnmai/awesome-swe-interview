# Engineering Scenarios Analysis

From [The 0→1 SWE Interview Playbook](https://valenx.org/books/swe)

Based on 3,500+ engineering scenarios extracted from 1,200+ job descriptions collected from builtin.com (January 2026).

## What I Extracted

Job postings describe what engineers will build, not just what skills they need. I pulled every concrete engineering scenario from the postings: the systems, features, and problems that companies need engineers to work on. After deduplication, I had 3,518 distinct scenarios.

These scenarios reveal what software engineers actually spend their time on. This matters for interview prep because system design questions draw from these real-world problems.

## Scenario Categories

### Building Scalable Web Applications (18.2%)

This is the largest single category. Companies need engineers to build, maintain, and scale web applications that serve thousands to millions of users.

Representative scenarios:

Build a real-time collaborative document editor supporting 500+ concurrent users per document. Handle conflict resolution, cursor presence, and offline synchronization. The system must work across web and mobile clients with sub-100ms sync latency.

Design and implement the checkout flow for an e-commerce platform processing 50K+ orders per day. Handle inventory reservation, payment processing, fraud detection, and order confirmation across multiple payment providers and currencies.

Build the content management system for a media company publishing 200+ articles per day. Support rich text editing, image optimization, SEO metadata, A/B testing of headlines, and scheduled publishing across time zones.

Migrate a monolithic Ruby on Rails application serving 2M monthly active users to a microservices architecture. Maintain zero downtime during migration. Ensure feature parity while improving deployment frequency from weekly to multiple times per day.

Build the notification system for a social platform. Handle push notifications, email, SMS, and in-app messages across 10M+ users. Support user preferences, rate limiting, batching, and delivery tracking. Ensure notifications arrive within 5 seconds of the triggering event.

Common technical challenges: state management, caching strategies, database schema design, authentication and authorization, responsive design, accessibility compliance, CDN configuration, error handling and user feedback.

### Designing and Maintaining APIs and Microservices (16.1%)

APIs and microservices are the backbone of modern software architecture. This category covers building, versioning, and operating services that other teams and external partners depend on.

Representative scenarios:

Design a public REST API for a payments platform. Handle authentication (OAuth 2.0, API keys), rate limiting (per-customer quotas), versioning (backward-compatible evolution), idempotency (safe retries), and comprehensive error responses. The API serves 1,000+ third-party integrations.

Build an internal service mesh connecting 40+ microservices. Implement service discovery, load balancing, circuit breaking, retry policies, and distributed tracing. Ensure the mesh adds less than 2ms of latency per hop.

Create a GraphQL gateway that federates data from 12 backend services into a unified API for frontend teams. Handle query complexity limits, batching, caching, and graceful degradation when upstream services are slow or unavailable.

Design the event-driven architecture for an order fulfillment system. Use Kafka to decouple order creation, payment processing, inventory management, shipping, and notification services. Handle exactly-once processing guarantees and dead letter queues for failed events.

Common technical challenges: API versioning strategies, backward compatibility, rate limiting, authentication, service-to-service communication patterns, distributed tracing, circuit breakers, retry with exponential backoff, idempotency keys.

### Data Pipeline and Processing Systems (12.4%)

Data engineering work appears in SWE roles, not just dedicated data engineer positions. Companies need engineers who can build systems that move, transform, and store data reliably.

Representative scenarios:

Build a real-time analytics pipeline processing 500M+ events per day from mobile and web clients. Ingest events through Kafka, transform with Flink, store in ClickHouse for real-time queries, and archive to S3 for batch analysis. Ensure end-to-end latency under 30 seconds.

Design the data synchronization layer between a legacy Oracle database and a new PostgreSQL-based microservices architecture. Handle bidirectional sync during the migration period. Ensure data consistency across both systems. Support rollback if the new system fails.

Build a feature engineering pipeline for an ML team. Extract features from raw event data, compute aggregations across multiple time windows (1 hour, 1 day, 30 days), store computed features in a low-latency feature store, and serve them to model inference endpoints at p99 latency under 10ms.

Create a GDPR compliance pipeline that identifies, exports, and deletes user data across 20+ services and 8 data stores within the legally required 30-day window. Handle cross-service dependencies and maintain audit logs for regulatory review.

Common technical challenges: exactly-once processing, schema evolution, backfill strategies, data quality monitoring, partitioning and compaction, cost optimization for storage and compute, late-arriving data handling.

### Mobile Application Development (9.3%)

Mobile development appears as a distinct category because the technical constraints and user expectations differ from web.

Representative scenarios:

Build a cross-platform mobile application using React Native that supports offline-first functionality. Users can create and edit content without connectivity. Changes sync automatically when the connection is restored, with conflict resolution for simultaneous edits.

Develop the real-time messaging feature for a social application. Handle message delivery, read receipts, typing indicators, media attachments, and group conversations. Support 100K+ concurrent connections per server. Optimize for battery consumption on mobile devices.

Build the camera and image processing pipeline for a photo-sharing application. Handle image capture, real-time filters, background removal, compression, and upload with resume capability. Optimize for devices ranging from budget Android phones to flagship iPhones.

Implement deep linking and attribution tracking for a mobile commerce application. Track user acquisition sources, handle deferred deep links for new installs, and attribute conversions across web and mobile surfaces.

Common technical challenges: offline-first architecture, state synchronization, battery optimization, app size management, platform-specific API differences, push notification reliability, app store review compliance.

### Cloud Infrastructure and Deployment (8.1%)

Infrastructure work that goes beyond traditional DevOps. These scenarios involve building the platforms and tools that other engineering teams use.

Representative scenarios:

Build an internal developer platform that standardizes service deployment across 200+ microservices. Provide self-service provisioning for compute, databases, message queues, and monitoring. Reduce the time from "new service idea" to "running in production" from 2 weeks to 2 hours.

Design the multi-region deployment strategy for a SaaS platform requiring 99.99% uptime. Handle data replication across regions, DNS-based failover, configuration management, and region-specific compliance requirements.

Build a cost optimization system that monitors AWS spending across 500+ accounts, identifies waste (idle instances, over-provisioned resources, unused storage), and recommends or automatically applies optimizations. Target: reduce monthly cloud spend by 20%.

Create a secrets management system that handles rotation, distribution, and audit of credentials across all production services. Integrate with Vault, support automatic rotation for database credentials and API keys, and provide emergency revocation capability.

Common technical challenges: infrastructure as code, multi-region architecture, cost optimization, security hardening, compliance automation, disaster recovery, capacity planning, service mesh configuration.

### Real-Time Systems (6.2%)

Systems that process and respond to events within strict time constraints.

Representative scenarios:

Build the real-time bidding system for an ad tech platform. Process 200K+ bid requests per second. Each bid must be evaluated and returned within 100ms. Handle dynamic pricing models, budget pacing, and fraud detection in real-time.

Design the live scoring and leaderboard system for a gaming platform. Process game events from 1M+ concurrent players. Update leaderboards within 1 second of score changes. Handle regional leaderboards, friend leaderboards, and global rankings.

Build the real-time fraud detection engine for a payments company. Analyze transaction patterns across 10M+ daily transactions. Flag suspicious activity within 500ms of transaction initiation. Balance false positive rate against fraud loss.

Implement the live video streaming infrastructure for a social platform. Handle ingestion from 50K+ concurrent broadcasters, transcoding to multiple quality levels, CDN distribution, and chat synchronization. Target glass-to-glass latency under 3 seconds.

Common technical challenges: low-latency processing, high-throughput event handling, time-series data, state management at scale, graceful degradation under load, jitter handling, clock synchronization.

### Search and Recommendation Systems (5.4%)

Building systems that help users find what they need and discover what they didn't know they wanted.

Representative scenarios:

Build the product search engine for an e-commerce platform with 10M+ SKUs. Handle typo correction, synonym matching, faceted filtering, relevance ranking, and personalized results. Return results within 200ms. Support queries in 12 languages.

Design the content recommendation system for a streaming platform. Combine collaborative filtering, content-based features, and contextual signals (time of day, device, viewing history) to generate personalized recommendations. Serve recommendations for 50M+ users with daily model updates.

Build an internal knowledge search system that indexes documentation, Slack messages, Jira tickets, and code repositories. Support natural language queries, relevance ranking, and access control based on team membership.

Common technical challenges: relevance tuning, cold-start problem, real-time personalization, A/B testing of ranking algorithms, embedding management, index freshness, multilingual support.

### Security and Compliance Systems (4.8%)

Building security features and compliance infrastructure.

Representative scenarios:

Implement the authentication and authorization system for a multi-tenant SaaS platform. Support SSO (SAML, OIDC), multi-factor authentication, role-based access control, and audit logging. Handle 50K+ authentication requests per minute.

Build the data classification and protection system for a healthcare platform. Automatically classify data by sensitivity level, enforce encryption policies, manage access controls, and generate compliance reports for HIPAA audits.

Design the vulnerability management pipeline that scans all production containers, dependencies, and infrastructure configurations. Prioritize findings by severity and exploitability. Integrate with engineering workflows so fixes are tracked to resolution.

Common technical challenges: zero-trust architecture, encryption key management, compliance automation, identity federation, threat detection, incident response automation, secure SDLC integration.

## Domain Distribution

The scenarios span multiple industries. Here is where the demand concentrates:

| Domain | Percentage of Scenarios |
|--------|------------------------|
| Finance and Payments | 18.7% |
| E-commerce and Retail | 16.3% |
| Enterprise SaaS | 14.8% |
| Healthcare and Life Sciences | 9.2% |
| Social and Media | 8.7% |
| Developer Tools and Infrastructure | 7.4% |
| Transportation and Logistics | 5.8% |
| Education and EdTech | 4.2% |
| Gaming and Entertainment | 3.8% |
| Real Estate and PropTech | 2.4% |
| Government and Civic Tech | 1.8% |
| Other | 6.9% |

Finance and payments leads because financial services companies hire aggressively for SWE roles and the technical challenges (correctness, compliance, performance, security) are demanding. E-commerce follows because the intersection of high traffic, real-time inventory, and payment processing creates complex engineering problems.

## Complexity Tiers

I categorized the scenarios by complexity to help candidates understand what level of work to expect:

Tier 1 (entry-level complexity, 24.3% of scenarios): Single-service features, CRUD operations, UI components, basic API endpoints, test writing, bug fixes. These appear in junior and some mid-level role descriptions.

Tier 2 (mid-level complexity, 42.8% of scenarios): Multi-service features, API design, database schema design, caching strategies, performance optimization, deployment pipelines. These dominate mid-level and some senior role descriptions.

Tier 3 (senior complexity, 27.4% of scenarios): Distributed system design, cross-team platform work, architecture decisions, migration strategies, scalability planning. These appear in senior, staff, and principal engineer descriptions.

Tier 4 (staff+ complexity, 5.5% of scenarios): Org-wide architecture, build-vs-buy decisions, technology strategy, multi-year migration planning, cross-functional platform development. These are rare in postings but common in actual staff+ work.

## Key Insights

The scenarios data tells me three things about interview preparation:

First, system design questions in interviews are drawn from these real-world problems. "Design a URL shortener" is a simplification of the real-time systems and API design categories. "Design a news feed" is a simplification of social/media recommendation systems. When you practice system design, practice with the complexity level that matches the role you are targeting.

Second, the most common engineering work is not algorithmically complex. It is architecturally complex. Building a checkout flow does not require dynamic programming. It requires understanding distributed transactions, eventual consistency, idempotency, and failure handling. Candidates who over-invest in algorithm practice and under-invest in system design understanding are preparing for the wrong challenge.

Third, domain knowledge matters more than postings suggest. A payments engineer who understands PCI compliance, settlement flows, and chargeback handling can design better payment systems than a generalist who only knows distributed systems theory. When choosing companies to interview with, consider whether your domain experience gives you an advantage.
