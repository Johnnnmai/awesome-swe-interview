# SWE Take-Home Assignments

Take-home assignments are growing in popularity as an alternative or supplement to live coding interviews. I found that roughly 25.0% of SWE interview processes now include some form of take-home component, with the trend accelerating in 2025-2026. Companies use them because they argue take-homes better simulate real work than solving algorithm puzzles under time pressure.

## Assignment Types

Based on my analysis of reported take-home assignments across job postings and candidate experiences, the distribution breaks down as follows:

Full-stack mini-app (40.0%+ of assignments)
Build a small but complete application. This is the most common type. Examples include a todo app with user authentication, a simple API with CRUD operations and a basic frontend, or a dashboard that consumes a public API. Time expectation is typically 3-6 hours, though actual time varies.

Algorithm and data structure challenge (25.0%)
More complex than a single LeetCode problem. You might be asked to implement a data structure (an LRU cache, a rate limiter, a simple database query engine) with clean code, documentation, and tests. These assignments test depth of understanding, not just whether you can reach the right answer.

System design document (15.0%)
Write a design document for a proposed system. Include requirements, architecture diagram, database schema, API design, scalability plan, and tradeoff analysis. This format is more common for senior roles. Time expectation: 2-4 hours.

Bug fix and code review (10.0%)
You receive an existing codebase with intentional bugs, poor practices, or missing features. Your job is to identify issues, fix them, and explain your changes. This tests your ability to read and improve unfamiliar code, which is closer to daily engineering work than writing from scratch.

Open source contribution (10.0%)
Some companies ask you to make a contribution to a specific open-source project (sometimes their own). This tests your ability to navigate existing codebases, follow contribution guidelines, and write code that meets community standards. Less common but growing among companies that maintain open-source projects.

## Real Examples

Full-stack app: "Build a book review application. Users should be able to create an account, search for books via a public API (Google Books or Open Library), add reviews with a 1-5 star rating and text, and see a feed of recent reviews. Use any stack you are comfortable with. Spend no more than 4-6 hours."

Algorithm challenge: "Implement a simple in-memory key-value store that supports GET, SET, DELETE, and COUNT operations. Additionally, implement transaction support (BEGIN, ROLLBACK, COMMIT) with nested transactions. Include tests."

System design doc: "Design a URL shortening service that can handle 10 million URLs created per day and 100 million redirects per day. Write a design document covering functional requirements, non-functional requirements, high-level architecture, database schema, API design, and scalability considerations."

Bug fix: "We have provided a Node.js/Express API for a simple task management system. The codebase has 5 bugs, 3 security vulnerabilities, and several code quality issues. Identify and fix as many as you can. Document your findings and fixes in a CHANGELOG file."

Open source: "Our open-source CLI tool has 3 open issues labeled `good-first-issue`. Pick one and submit a pull request. Follow our contribution guidelines in CONTRIBUTING.md."

## What Companies Evaluate

Code quality and organization
Clean code, consistent style, meaningful names, logical file structure. They check whether your code looks like production code or a hackathon project. Linting and formatting tools configured (ESLint, Prettier, Black, etc.) are a positive signal.

Testing
Presence and quality of tests is one of the strongest signals. I found that including tests separates the top 20.0% of submissions from the rest. Unit tests for core logic, integration tests for API endpoints, and edge case coverage all matter.

Documentation
A clear README with setup instructions, architectural decisions, and known limitations. You do not need a novel, but "clone, run `npm install`, run `npm start`" should work on the first try for anyone evaluating your submission.

Error handling
How does your application handle bad input, network failures, and edge cases? Graceful error handling with meaningful error messages scores much better than uncaught exceptions.

Git history
Some evaluators look at your commit history. Small, logical commits with clear messages ("add user authentication endpoint," "fix pagination off-by-one error") signal professionalism. A single giant commit suggests you wrote everything at the end.

Technology choices
Can you justify your stack choices? If you chose React over plain HTML, why? If you used SQLite instead of PostgreSQL, was that a reasonable choice for the scope? Evaluators want to see that you make intentional decisions rather than defaulting to whatever you last used.

## How to Prepare

Set up project templates in advance. Have boilerplate ready for your preferred stack (a basic Express/FastAPI/Spring Boot app with testing configured, linting set up, and a clean structure). This saves 30-60 minutes of setup time during the actual assignment.

Practice with timed exercises. Give yourself 4 hours to build a small app from scratch. The time pressure of a real take-home is different from building a personal project with no deadline.

Read the instructions twice. I found that a significant percentage of rejections come from missing a requirement in the instructions. If they say "use TypeScript," do not submit JavaScript. If they say "include a Dockerfile," include a Dockerfile.

## Format and Submission

Most companies expect:
- A GitHub repository (often private, shared with specific evaluators)
- A README with setup instructions, assumptions, and architecture notes
- A working application that can be run locally with minimal setup
- Tests that pass
- Clean git history

Submission timeline is typically 3-7 days from receiving the assignment. Most candidates complete it within the first 2-3 days. Submitting on day 7 is not penalized, but submitting significantly past the deadline without communication is.

## Common Mistakes

Over-engineering the solution. Adding a microservices architecture, Kubernetes deployment, GraphQL subscriptions, and a CI/CD pipeline to a todo app signals poor judgment about scope. Build what is asked, build it well, and document what you would add with more time.

No tests. This is the single most common mistake I found. Even a few well-written tests dramatically improve your submission. Evaluators notice the absence of tests immediately.

Not handling the happy path reliably. If the core functionality does not work, nothing else matters. Make sure the basic use case works perfectly before adding features.

Ignoring the README. "README.md: TODO" is a surprisingly common submission artifact. Write a real README. Explain how to set up and run the project, what assumptions you made, and what you would improve with more time.

Copy-pasting from tutorials without understanding. Evaluators recognize tutorial code. If your project structure matches a popular tutorial exactly but you cannot explain why you chose that structure in the follow-up interview, it hurts more than it helps.

Spending too much time. Companies typically say 3-6 hours, and they mean it. If you spend 20 hours, you might produce a more polished result, but you have also demonstrated poor time management. Scope your work to fit the time budget.

Not testing on a clean environment. Your project works on your machine because of globally installed packages, environment variables, or cached dependencies. Test your setup instructions on a fresh checkout. Better yet, test it in a Docker container.

## The Follow-Up Interview

Most companies follow the take-home with a review session (30-45 minutes) where you walk through your code with an engineer. Be prepared to:

Explain your architecture decisions. Why did you structure the code this way? What tradeoffs did you consider?

Walk through a specific piece of code. The interviewer may pick a function and ask you to explain it line by line. Make sure you understand every line you submitted.

Discuss extensions. How would you add caching? How would you scale this to handle 10x the traffic? What would you change if this were a production service?

Address known limitations honestly. If you know your error handling is incomplete or your test coverage has gaps, say so proactively. Self-awareness scores better than defensiveness.

Respond to code review feedback. The interviewer may point out issues. Respond the way you would in a real code review: acknowledge valid points, explain your reasoning for intentional choices, and show willingness to improve.

## Should You Do Take-Homes?

A common debate in the SWE community: are take-homes worth the time investment? My view based on the data:

Take-homes favor candidates who write clean, production-quality code but underperform in live coding under pressure. If that describes you, seek out companies that use take-homes.

Take-homes are time-consuming when you are interviewing at many companies simultaneously. If you have five take-homes due in the same week, quality will suffer. Prioritize based on company interest.

Take-homes can be a positive signal about the company's hiring culture. Companies that invest in designing a thoughtful take-home are often more intentional about their engineering practices overall.

If a company's take-home is unpaid and exceeds 8 hours of expected work, that is a yellow flag about how they value your time. Increasingly, companies are paying for take-home time ($100-$500) or capping expected effort at 3-4 hours.
