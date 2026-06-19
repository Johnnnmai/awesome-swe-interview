# Webinar 4: SWE Take-Home Assignments

Date: March 9, 2026

## Overview

This session analyzes 85 take-home coding assignments collected from companies of various sizes between 2024 and 2026. Take-homes are an alternative to live coding interviews used by roughly 25.0-30.0% of companies, more common at startups and mid-size companies than at FAANG.

Understanding what evaluators actually look at helps you allocate your time on the right things instead of gold-plating features nobody checks.


## What Companies Send

Assignment types (across 85 samples):
- Build a small feature or API: 41.2% of assignments. "Build a REST API for a task manager with CRUD operations and user authentication."
- Extend an existing codebase: 24.7%. You receive a starter project and add a feature, fix bugs, or refactor.
- Data processing or algorithm challenge: 18.8%. Parse a dataset, implement a specific algorithm, or optimize a solution.
- Frontend implementation: 15.3%. Build a UI component, implement a design mockup, or create an interactive data visualization.

Time expectations:
- Stated time limit: 72.9% of assignments specified a recommended time (typically 3-6 hours)
- Actual completion time (self-reported by candidates): averaged 6.8 hours, with a range from 2 to 15 hours
- The gap between stated and actual time is real. Companies know it takes longer than they say.


## What Evaluators Actually Check

I surveyed engineering managers and senior engineers who review take-home submissions. Their evaluation priorities, ranked:

1. Code works correctly (95.0% listed as top priority). Submissions that do not run are immediately rejected. Test this on a clean machine or container before submitting.

2. Code readability (82.0%). Consistent naming, clear function boundaries, no 200-line functions. Evaluators scan code quickly; readable code gets a more favorable read.

3. Test coverage (71.0%). Having tests at all puts you in the top 30.0% of submissions. Unit tests for core logic and one or two integration tests are sufficient.

4. Error handling (64.0%). How does your code handle bad input, network failures, or edge cases? `try/catch` with meaningful error messages, not swallowed exceptions.

5. README quality (58.0%). Setup instructions, design decisions, and known limitations. A good README saves the evaluator 10 minutes of guessing and creates goodwill.

6. Git history (42.0%). Atomic commits with clear messages show your development process. One giant commit labeled "done" raises questions.

7. Architecture decisions (38.0%). For larger assignments, how you structure the code matters. Separation of concerns, dependency injection, and clear module boundaries.


## Common Mistakes

Over-engineering: adding features not requested, implementing a full CI/CD pipeline, or building an admin dashboard when the assignment asked for a single API. Evaluators want to see you solve the stated problem well, not that you can add scope.

No README: 34.0% of submissions had no README or a default template. This is the easiest improvement you can make. Explain what you built, how to run it, and what tradeoffs you made.

No tests: 55.0% of submissions had zero tests. Even 5-10 unit tests covering the core logic signals engineering discipline.

Ignoring the time limit: spending 15 hours on a "4-hour" assignment and submitting perfect code does not impress. It signals you either cannot scope work or you are misrepresenting the effort.

Not handling errors: happy-path-only code fails the first time an evaluator tries unexpected input. Add input validation and error responses for common failure modes.


## How to Stand Out

Write a design decisions section in your README. Explain 2-3 technical choices: why you picked this database, why you structured the API this way, what you would change with more time. This gives the evaluator insight into your thinking, which is what they are actually trying to assess.

Include a "what i would improve" section. Acknowledge the limitations honestly. "With more time, i would add pagination, implement caching, and add integration tests" shows awareness without requiring you to actually build everything.

Deploy it. If the assignment is a web application, deploy it somewhere free (Vercel, Railway, Render). A live URL removes all setup friction for the evaluator and demonstrates you can ship.


## Resources

- [The 0 to 1 SWE Interview Playbook](https://valenx.org/books/swe)
- [How to write a technical README](https://www.makeareadme.com/)
- [GitHub: take-home assignment examples](https://github.com/topics/take-home-assignment)
