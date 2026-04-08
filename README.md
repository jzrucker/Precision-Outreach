# Precision Outreach

**Live demo:** [jzrucker.github.io/Precision-Outreach](https://jzrucker.github.io/Precision-Outreach/)

---

## What it does

Precision Outreach is a browser-based tool that takes screenshots from a company's LinkedIn People page, identifies the right person to contact after you've applied for a role, and generates a targeted outreach message under 300 characters.

No scraping. No automation. No mass messaging. One person. One message. Under 300 characters.

---

## Why it exists

Cold portal applications convert at near zero. The research backs this up, and so does lived experience running dozens of applications across AI-forward companies.

What actually works is direct outreach to the right human — someone senior enough to matter, with enough internal pull to move your application forward. The problem is that identifying that person takes 20 minutes of LinkedIn scrolling per company, and writing something that doesn't read like a template takes another 10.

This tool compresses both steps to under 2 minutes.

The insight that makes it possible: LinkedIn has no public API for outreach by design, but a human can take a screenshot. Upload two screenshots of the company's People page and the AI reads every visible name, title, and bio snippet — applying a targeting hierarchy to pick the right contact, then writing directly to that person.

---

## How it works

1. **Apply first.** Submit through the job portal. Always.
2. **Screenshot.** Go to the company's LinkedIn People page. Filter by country. Screenshot the default view. Then search `hiring` or `recruiting` in the employee search bar and screenshot those results too.
3. **Upload and generate.** Drop the screenshots into the tool along with the company name and role. The AI scans every visible person and picks one — not the most junior, not the CEO unless the company is tiny, not a consultant or fractional advisor. Someone with actual internal pull who is likely involved in or adjacent to the hiring decision.
4. **Send.** Three message variants are generated, all under 300 characters. Copy the one that fits. Send it on LinkedIn via "Connect with a note." Follow up once after 5 days if no response.

---

## Targeting logic

The AI applies a strict priority order when selecting who to contact — embedded in the model, not exposed in the UI:

**Priority order:**
1. Anyone whose visible bio or snippet explicitly mentions "hiring" or "building our team" — immediate top pick, strongest signal
2. Senior internal HR/Talent: Head of Talent, VP People, Director of Recruiting, Senior Talent Partner, Senior Recruiter — full-time employees only, not consultants
3. Hiring manager or team lead whose function directly matches the role applied for, if no HR layer exists
4. Founder or relevant exec only at very small companies (<15 people) with no other option

**Seniority signals — weighted in selection:**
- "ex-[Company]" or "former [Title]" visible in snippet = established professional, prioritized
- Snippet implies multiple years of senior experience = positive signal
- Snippet looks like first or second job = deprioritized

**Never selected:**
- Anyone with Advisor, Consultant, Fractional, or Contractor in title — less internal pull than a full-time employee
- Anyone with Associate, Coordinator, Analyst, or Intern in title
- Anyone who appears early in their career or recently hired
- The CEO unless the company is clearly under 15 people

---

## The 300 character constraint

This is the core product opinion. LinkedIn's "Connect with a note" option is the only outreach mechanism that doesn't require an existing connection — and most people fill it with four sentences of generic filler that nobody reads.

The 300 character constraint is enforced deliberately. It forces a single specific thing about the company connected directly to a single specific thing about yourself. That compression is what makes the message feel human rather than templated. The tool generates three variants — Primary, Direct, and Hook — so you can choose the one that fits your voice.

---

## Built with

- Claude API (claude-sonnet, vision + text for screenshot analysis)
- Vanilla JavaScript — zero dependencies, zero build step
- User supplies their own Anthropic API key — never stored, session only
- Deployed on GitHub Pages

---

## Results

Built and deployed in one afternoon as a direct response to recruiter feedback that I needed more personal projects and startup experience. Used it the same day on a live target — the tool surfaced the Head of AI Strategy at the company as the recommended contact, functionally aligned with the exact role applied for, with a 283-character message ready to send.

It won't convert every time. If it converts 10% of outreaches into a real conversation, it's already 10x better than the portal alone.

---

*Part of a broader portfolio of practical AI tools built for real workflows. See also: K-1 PDF Summarizer · Autonomous Trading Agent*

---

*Part of a broader portfolio of practical AI tools built for real workflows. See also: [K-1 PDF Summarizer](https://github.com/jzrucker) · Autonomous Trading Agent*
