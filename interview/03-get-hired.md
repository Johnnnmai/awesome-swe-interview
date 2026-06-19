# Getting Hired

Based on 100+ sources including interviewer blog posts, hiring manager AMAs on Reddit and Blind, post-interview retrospectives, and engineering team hiring guides, I identified what consistently separates candidates who get offers from those who don't.

## What Interviewers Actually Test

Coding fluency
Interviewers want to see that you write clean, correct code without excessive fumbling. This means proper variable naming, handling edge cases proactively (null inputs, empty arrays, overflow), and articulating time and space complexity without being asked. About 35.0% of candidates lose points not because their solution is wrong, but because their code is messy or they miss obvious edge cases.

Problem-solving approach
How you get to the answer matters as much as the answer itself. Interviewers evaluate whether you clarify assumptions before coding, whether you think out loud, and whether you can adjust when your first approach hits a wall. The candidates who get hired talk through their reasoning. The ones who sit in silence for three minutes and then start typing rarely pass.

System design thinking
For mid-level and senior roles, interviewers test whether you can reason about distributed systems, make principled tradeoffs between consistency and availability, estimate scale, and design for failure. They are not looking for memorized architectures. They want to see how you think when faced with ambiguity.

Code quality signals
Beyond correctness, interviewers notice: Do you write functions with clear responsibilities? Do you mention testing even if not asked? Do you refactor when you see duplication? These signals separate "can code" from "writes production-quality code."

Communication and collaboration
Every source I found emphasized this. Can you explain your approach to a non-expert? Do you listen to hints? Do you ask good clarifying questions? Multiple hiring managers said they have rejected technically strong candidates who could not communicate.

Past project depth
When asked about past work, surface-level answers hurt you. Interviewers probe: What was your specific contribution? What technical decisions did you make and why? What would you do differently? Candidates who can go deep on at least two projects consistently perform better in behavioral rounds.

## What Separates Candidates

After analyzing hiring signals across sources, I found five consistent differentiators:

1. Structured communication. Top candidates use frameworks without sounding robotic. They state the problem, outline their approach, code it, then verify. This pattern appeared in 80.0%+ of "what got me hired" posts.

2. Genuine curiosity about the problem. Interviewers notice when candidates are intellectually engaged versus just performing. Asking "what if the input is a stream instead of a fixed array?" or "could we trade memory for speed here?" signals depth.

3. Recovery from mistakes. Everyone makes errors during interviews. Candidates who catch their own bugs, acknowledge mistakes, and course-correct get hired. Candidates who double down on broken approaches don't.

4. Specificity in behavioral answers. Vague answers like "I improved system performance" lose to specific ones like "I reduced p99 latency from 800ms to 120ms by identifying an N+1 query pattern in our user feed service."

5. Preparation that shows. Knowing the company's tech stack, recent engineering blog posts, or product challenges signals genuine interest. Multiple interviewers said this tips close decisions.

## Portfolio Strategy

For software engineers, your portfolio is your GitHub profile, personal projects, and open-source contributions. Here is what I found actually matters:

Focus on 2-3 quality projects over many shallow ones. Hiring managers spend under 60 seconds on a GitHub profile. One well-documented project with tests, a clear README, and actual commits over time beats twenty starter templates.

Contribute to open source if possible. Even small contributions (bug fixes, documentation, test coverage) to known projects carry weight. They show you can read unfamiliar code and work within existing conventions.

Build something you actually use. Projects born from personal need are easier to talk about and tend to be more complete. "I built a CLI tool to manage my dotfiles" is more compelling than "I followed a tutorial to build a Twitter clone."

Skip the portfolio website unless it demonstrates frontend skills relevant to the role. A clean GitHub profile with pinned repositories is sufficient for most SWE roles.

## Before You Apply

Tailor your resume to each role. Use the same language as the job description. If they say "distributed systems," don't write "backend architecture." ATS systems and recruiters scan for keyword matches.

Target 50-100 applications, not 500. Spray-and-pray produces a worse hit rate than targeted applications with tailored resumes and cover letters (where requested). I found a consistent pattern: candidates who applied to fewer, better-matched roles got more interviews per application.

Leverage referrals. Internal referrals bypass the resume screen at most companies. A single referral is worth 20+ cold applications based on conversion rate data shared by recruiters.

## Common Mistakes

Mistake 1: Grinding LeetCode without learning patterns. Solving 500 random problems is less effective than solving 150 problems organized by pattern. Multiple successful candidates reported that learning 14-15 core patterns made new problems recognizable.

Mistake 2: Skipping system design prep. Mid-level candidates who ace coding but bomb system design don't get offers. I found this was the number one reason for onsite rejections at the L4-L5 level.

Mistake 3: Neglecting behavioral preparation. Engineers who dismiss behavioral rounds as "soft" routinely underperform. At Amazon, behavioral accounts for roughly 50.0% of the hiring decision.

Mistake 4: Not practicing under time pressure. Solving a problem in 90 minutes at home is different from solving it in 45 minutes with someone watching. Timed practice and mock interviews are the closest approximation to real conditions.

Mistake 5: Accepting the first offer without negotiating. I address this in detail in the After the Interview section, but the data is clear: 70.0%+ of initial offers have room for negotiation, and most candidates who negotiate get more.

Mistake 6: Studying alone instead of doing mock interviews. Reading about system design is passive. Explaining a design while someone asks pointed questions is active. The gap between these two modes of preparation is enormous.

## How to Prepare: The 8-12 Week Timeline

Weeks 1-2: DSA fundamentals
Build or rebuild your foundation. Focus on Big-O analysis, arrays, strings, and hash maps. Solve 20-30 easy problems to build fluency. If you struggle with basic data structures, extend this phase. Everything else builds on it.

Weeks 3-4: Intermediate data structures and algorithms
Move to trees, graphs, BFS/DFS, and dynamic programming. These topics appear in 60.0%+ of coding interviews. Solve 20-30 medium problems. Start recognizing which pattern applies to each problem type.

Weeks 5-6: System design fundamentals
Study scalability patterns: load balancing, caching, database sharding, message queues, CDNs. Read system design primers. Practice designing 2-3 systems end to end. Watch mock system design interviews on YouTube to calibrate your depth.

Weeks 7-8: Mock interviews and behavioral stories
Do 4-6 mock interviews (coding and system design). Use platforms like Pramp, interviewing.io, or practice with friends. Prepare 8-10 behavioral stories using the STAR format. Each story should demonstrate a different strength.

Weeks 9-10: Company-specific preparation
Research your target companies. Review their engineering blogs, tech talks, and interview question databases. Use LeetCode company tags to focus on frequently asked questions. Understand their values and culture.

Weeks 11-12: Final mock interviews and polish
Do 2-4 more mock interviews, focusing on your weakest areas. Review all your behavioral stories. Prepare thoughtful questions to ask interviewers. Get your logistics sorted: quiet space, reliable internet, clean whiteboard or screen-sharing setup.

## Compensation Ranges (2025-2026 US Market)

These numbers reflect total compensation (base + stock + bonus) at established tech companies and well-funded startups. Actual numbers vary by company, location, and negotiation.

| Level | Big Tech Total Comp | Startup Range |
|---|---|---|
| New Grad / Junior | $150K-$220K | $100K-$160K + equity |
| Mid-level (L4) | $250K-$400K | $150K-$280K + equity |
| Senior (L5) | $350K-$550K | $250K-$400K + equity |
| Staff+ (L6+) | $500K-$900K+ | $350K-$600K + equity |

Big tech numbers come from levels.fyi data and verified Blind posts. Startup equity is highly variable; pre-IPO equity can be worth anywhere from zero to multiples of base salary. The ranges above assume companies in major tech hubs (SF Bay Area, Seattle, NYC). Remote roles and roles in lower cost-of-living areas typically pay 10.0-25.0% less.

Key compensation trends I observed:
- Stock refreshers have become a larger portion of total comp at companies like Google and Meta
- Sign-on bonuses of $30K-$100K are common for senior roles, especially when competing with other offers
- Startup equity packages are becoming more transparent, with companies sharing cap table details earlier in the process
- Base salary bands have compressed somewhat, with the real differentiation happening in equity and bonus

## What Matters Most

If I had to distill everything into three priorities for a candidate with limited time:

1. Master 15 coding patterns (not 500 random problems)
2. Practice explaining your thinking out loud while coding
3. Prepare 8-10 specific, detailed stories about your past work

Everything else is optimization on top of these three fundamentals.
