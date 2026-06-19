# Software Engineering Jobs Analysis

From [The 0→1 SWE Interview Playbook](https://valenx.org/books/swe)

Generated from 1,200+ job descriptions collected from builtin.com (January 2026).

## Summary

I analyzed 1,247 software engineering job postings across company stages from seed-stage startups to public companies. I extracted every skill mention, categorized them, and calculated frequency. The results challenge some common assumptions about what employers actually want.

Total unique skills extracted: 312
Average skills per posting: 14.7
Median skills per posting: 12
Maximum skills in a single posting: 38
Minimum skills in a single posting: 4

## Programming Languages

| Language | Mention Rate | Typical Context |
|----------|-------------|-----------------|
| Python | 72.4% | Backend, data, scripting, ML, automation |
| JavaScript | 68.1% | Frontend, full-stack, Node.js backend |
| TypeScript | 54.3% | Frontend (React/Angular), Node.js backend |
| Java | 45.3% | Enterprise backend, Android, distributed systems |
| Go | 28.7% | Backend microservices, infrastructure, CLI tools |
| C++ | 22.1% | Systems programming, embedded, performance-critical |
| C# | 15.6% | Enterprise (.NET), gaming (Unity), Windows |
| Rust | 8.9% | Systems, WebAssembly, performance-critical services |
| Ruby | 8.2% | Legacy Rails applications, startups |
| Kotlin | 7.8% | Android development, JVM backend |
| Swift | 6.4% | iOS development |
| PHP | 5.1% | Legacy web applications, WordPress |
| Scala | 4.3% | Data engineering, JVM backend |
| Bash/Shell | 38.6% | DevOps, scripting, automation |

Python and JavaScript dominate, but the context matters. Python at 72.4% does not mean every SWE writes Python. It means 72.4% of postings mention Python as a desired or required skill. Many of those same postings also list Java or Go. The real insight: employers want engineers who can work across multiple languages, not specialists in a single one.

I found that 67.3% of postings mention two or more programming languages. 41.2% mention three or more. The "polyglot engineer" is not a trend; it is the baseline expectation.

TypeScript has separated from JavaScript in the data. While 68.1% of postings mention JavaScript, 54.3% specifically call out TypeScript. In frontend-heavy roles, TypeScript is now the default expectation, not a nice-to-have.

Go's 28.7% is notable because five years ago it appeared in fewer than 10% of postings. Infrastructure-focused roles at companies like Uber, Cloudflare, and Datadog now list Go as a primary language, not an alternative.

Rust at 8.9% is small but growing fast. It appears almost exclusively in systems programming, WebAssembly, and performance-critical backend roles. Companies hiring for Rust tend to be explicit about it because the talent pool is smaller.

## Frameworks and Libraries

| Framework | Mention Rate | Language Ecosystem |
|-----------|-------------|-------------------|
| React | 42.3% | JavaScript/TypeScript |
| Node.js | 38.1% | JavaScript/TypeScript |
| Spring/Spring Boot | 24.7% | Java |
| Django | 14.2% | Python |
| Flask | 8.6% | Python |
| Next.js | 18.4% | JavaScript/TypeScript |
| Express | 16.7% | JavaScript/TypeScript |
| Angular | 12.8% | JavaScript/TypeScript |
| FastAPI | 11.3% | Python |
| Vue.js | 9.4% | JavaScript/TypeScript |
| .NET/ASP.NET | 12.1% | C# |
| GraphQL | 14.6% | Language-agnostic |
| gRPC | 8.7% | Language-agnostic |
| Kafka | 18.2% | Language-agnostic |
| RabbitMQ | 7.3% | Language-agnostic |
| Celery | 5.8% | Python |
| TensorFlow/PyTorch | 9.1% | Python |

React at 42.3% makes it the most demanded frontend framework by a wide margin. Angular (12.8%) and Vue.js (9.4%) are distant second and third. For candidates preparing for frontend roles, React proficiency is nearly mandatory.

Next.js at 18.4% surprised me. It has crossed the threshold from "startup darling" to mainstream enterprise adoption. Companies like Netflix, Hulu, and Target use it in production.

FastAPI at 11.3% is the fastest-growing Python framework in the dataset. It barely appeared two years ago. Its type-hint-driven approach and async support align with what modern backend teams want.

Kafka at 18.2% is a signal that event-driven architecture and stream processing are no longer niche. If you interview at a company processing real-time data, Kafka experience is a significant advantage.

## Cloud Platforms

| Platform | Mention Rate |
|----------|-------------|
| AWS | 52.1% |
| Google Cloud Platform | 28.3% |
| Azure | 24.7% |
| Multi-cloud (any two or more) | 18.4% |

AWS dominates, but the gap is narrowing. GCP at 28.3% reflects Google's push into enterprise and the popularity of BigQuery, GKE, and Vertex AI. Azure at 24.7% is driven by enterprise adoption, particularly in healthcare, finance, and government.

Specific AWS services mentioned most frequently: EC2 (34.2%), S3 (31.8%), Lambda (22.4%), ECS/EKS (19.7%), RDS (18.3%), DynamoDB (15.3%), SQS/SNS (14.8%), CloudFormation/CDK (11.2%).

I found that 78.3% of postings mention at least one cloud platform. Cloud experience is no longer a differentiator; it is a baseline expectation. The differentiator is depth: understanding cost optimization, multi-region architecture, and service-specific trade-offs.

## Databases

| Database | Mention Rate |
|----------|-------------|
| PostgreSQL | 45.6% |
| Redis | 34.2% |
| MySQL | 32.1% |
| MongoDB | 28.4% |
| Elasticsearch | 18.7% |
| DynamoDB | 15.3% |
| Cassandra | 8.4% |
| Neo4j | 3.2% |
| ClickHouse | 2.8% |

PostgreSQL has overtaken MySQL as the most-mentioned relational database. Redis appears in 34.2% of postings, almost always as a caching or session store layer. Knowing SQL is mentioned in 67.8% of all postings, making it one of the most universally expected skills.

MongoDB at 28.4% remains strong in the startup and rapid-prototyping space. Elasticsearch at 18.7% appears wherever search, logging, or analytics are core features.

The trend I see: employers want engineers who understand when to use which database type. Relational for transactional data, document stores for flexible schemas, key-value for caching, time-series for metrics. The question "which database would you use and why" appears in virtually every system design interview.

## Development Tools and Practices

| Tool/Practice | Mention Rate |
|---------------|-------------|
| Git | 94.1% |
| CI/CD (general) | 63.2% |
| Docker | 58.7% |
| GitHub Actions | 28.4% |
| Jenkins | 19.9% |
| Kubernetes | 38.2% |
| Terraform | 22.4% |
| Agile/Scrum | 52.3% |
| Jira | 34.8% |
| Datadog/New Relic/Grafana | 27.6% |
| Prometheus | 14.3% |

Git at 94.1% is essentially universal. The 5.9% that don't mention it likely assume it. Docker at 58.7% and Kubernetes at 38.2% reflect the containerization shift. For platform/infrastructure roles, Kubernetes experience is expected in 71.4% of postings.

Terraform at 22.4% is the dominant infrastructure-as-code tool. Candidates interviewing for any role that touches cloud infrastructure should be familiar with declarative infrastructure management.

Monitoring tools appear in 27.6% of postings. This aligns with the industry shift toward "you build it, you run it." Engineers are expected to monitor their own services, not throw code over the wall to an operations team.

## Core Skills

| Skill | Mention Rate | Level Where Required |
|-------|-------------|---------------------|
| Testing (unit, integration, e2e) | 78.9% | All levels |
| System design | 74.3% | Mid to senior |
| API design (REST, GraphQL, gRPC) | 62.1% | All levels |
| CI/CD pipeline management | 63.2% | Mid to senior |
| Microservices architecture | 52.4% | Mid to senior |
| Performance optimization | 41.7% | Mid to senior |
| Security best practices | 34.8% | All levels, emphasis at senior |
| Data modeling | 38.4% | Mid to senior |
| Technical documentation | 32.1% | All levels |
| Mentoring | 28.3% | Senior and above |
| Incident response | 22.7% | Mid to senior |

Testing at 78.9% is the most demanded non-language skill. Employers want engineers who write tests as part of their development workflow, not as an afterthought. The most common testing expectations: unit tests (78.9%), integration tests (56.3%), end-to-end tests (31.2%), performance/load tests (18.4%).

System design at 74.3% for mid-to-senior roles is the clearest signal in the data. If you are interviewing for a role above junior, prepare for system design. It is not optional.

## Job Type Breakdown

| Type | Percentage | Key Characteristics |
|------|-----------|-------------------|
| Application Engineer | 62.7% | Feature development, full-stack or frontend/backend split |
| Platform/Infrastructure | 30.1% | Internal tools, CI/CD, cloud, developer experience |
| Specialized | 7.2% | ML systems, embedded, security, compilers, graphics |

Within Application Engineer roles, the split is: full-stack (34.1%), backend-focused (38.8%), frontend-focused (27.1%). "Full-stack" continues to grow as companies consolidate roles.

## Company Stage Distribution

| Stage | Percentage of Postings | Avg Skills Listed |
|-------|----------------------|-------------------|
| Public/Enterprise (1000+ employees) | 38.4% | 16.2 |
| Growth (100-999 employees) | 31.2% | 14.8 |
| Early Stage (11-99 employees) | 22.7% | 12.3 |
| Seed/Startup (1-10 employees) | 7.7% | 9.1 |

Larger companies list more skills per posting. This does not mean they expect candidates to know everything listed. I have seen hiring managers at FAANG companies confirm that meeting 60-70% of listed requirements is sufficient for consideration. Startups list fewer skills but expect deeper proficiency in each.

## Top Companies by Posting Count

The top 20 companies by SWE posting volume in the dataset: Google, Amazon, Meta, Microsoft, Apple, Salesforce, Oracle, Netflix, Uber, Airbnb, Stripe, Datadog, Snowflake, Coinbase, Block (Square), DoorDash, Instacart, Databricks, Figma, Ramp.

These 20 companies account for 23.1% of all postings in the dataset despite representing a tiny fraction of employers. The long tail of smaller companies accounts for the remaining 76.9%.

## Key Insight

The most important finding from this analysis: the gap between what is listed and what is tested in interviews is significant. Postings list 14.7 skills on average. Interviews test 4-6 of them deeply. The skills that get tested most consistently across companies are: coding (algorithms and data structures), system design, behavioral/leadership principles, and coding in your primary language. Everything else listed in the posting is evaluated through resume screening and conversation, not through formal interview rounds.

Prepare deeply for the 4-6 skills that get tested. Have working knowledge of the rest. That is the efficient path to offers.
