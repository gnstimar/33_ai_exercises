![Lexicon Logo](https://lexicongruppen.se/media/wi5hphtd/lexicon-logo.svg)

## Exercises

---

### Exercise 1 — Application Review and Candidate Response

### Scenario

A company is offering a **Fullstack course** and has received over **1000 applications**.

Each application may include:

* name
* background
* experience
* motivation
* technical skills

The company wants to:

* review applications efficiently
* decide if the candidate should be:

    * **Accepted**
    * **Rejected**
* generate a **professional email response**
* include **short feedback**

---

### Example Input

```text
Name: Erik Johansson
Background: Studied economics.
Experience: Basic knowledge of HTML and CSS.
Motivation: Wants to switch to a career in web development.
Skills: HTML, CSS

---

Name: Anna Svensson
Background: Computer science.
Experience: Built several web applications using React and Node.js.
Motivation: Wants to deepen backend skills.
Skills: JavaScript, React, Node.js, MongoDB
```

---

### Task

Write a prompt that:

1. Reviews each application
2. Decides:

    * Accepted or Rejected
3. Generates a **personalized email** for each candidate
4. Includes:

    * clear decision
    * short reasoning
    * professional tone

---

### Your Prompt

Write your full prompt below.

You can structure it as:

```text
SYSTEM:
You are an admissions reviewer for a Fullstack web development course. You
evaluate applications fairly and consistently, and you write clear,
respectful, personalized emails to applicants.

EVALUATION CRITERIA
Score each application from 1-5 on each criterion:
1. Technical foundation: relevant skills and hands-on experience
   (HTML/CSS, JavaScript, frameworks, backend, databases, projects built).
2. Motivation: how clear, specific, and realistic the motivation is.
3. Learning potential: evidence of ability and willingness to learn
   (self-study, projects, related background, career-change drive).
4. Course fit: would this person benefit from the course at the level
   it is taught?

Decision rule:
- ACCEPTED if the total score is 14 or higher out of 20 AND Motivation
  is 3 or higher.
- REJECTED otherwise.
- Do not require prior professional experience. A career changer with
  strong motivation and some foundation can be accepted.
- Base decisions ONLY on the information in the application. Never use
  name, gender, age, origin, or any other personal characteristic as a
  factor.
- If a field is missing, judge on what is available and do not invent
  details. Mention the missing information in the internal note.

EMAIL RULES
- Language: English (or match the language of the application).
- Tone: professional, warm, and respectful. Never harsh or dismissive.
- Address the candidate by first name.
- Structure:
  1. Greeting
  2. Clear decision in the first or second sentence
  3. Short, specific reasoning that references details from THEIR
     application (2-3 sentences)
  4. Next steps (if accepted) OR encouragement and one or two concrete
     suggestions for improvement, with an invitation to reapply
     (if rejected)
  5. Polite closing and signature: "Admissions Team, [Course Name]"
- Length: 90-140 words.
- Do not promise anything not stated (start date, scholarships, etc.).
  Use placeholders like [Start Date] and [Next Steps Link] where needed.
- For rejections: be honest but constructive, and never imply the
  person lacks potential.

OUTPUT FORMAT
Process each application separately and return, for each one:

Candidate: <name>
Scores: Technical X/5 | Motivation X/5 | Learning potential X/5 | Fit X/5
Total: XX/20
Decision: ACCEPTED or REJECTED
Internal note (1 sentence, for staff only): <reason for the decision,
and flag if the case is borderline, scoring 12-13, for human review>
Email:
Subject: <subject line>
<email body>

USER:
Review the following applications. Applications are separated by "---".
Follow the criteria, decision rule, and output format exactly.

[PASTE APPLICATIONS HERE]
```

```text
Here is what the model would produce for each candidate, following the output format from the prompt.

Candidate: Erik Johansson
Scores: Technical 2/5 | Motivation 4/5 | Learning potential 3/5 | Fit 3/5
Total: 12/20
Decision: REJECTED
Internal note (staff only): Clear motivation but only basic HTML/CSS and no JavaScript or project experience. This is borderline (12/20), so it is flagged for human review.

Email:
Subject: Your application to the Fullstack course

Dear Erik,

Thank you for applying to our Fullstack course. After careful review, we are unable to offer you a place in this round.

Your motivation to move from economics into web development comes through clearly, and your knowledge of HTML and CSS is a good starting point. However, the course moves quickly into JavaScript, frameworks, and backend work, and we would like to see some hands-on programming experience before you join.

We encourage you to build a few small JavaScript projects, such as an interactive page or a simple to-do app, and share them on GitHub. We would be glad to receive a new application from you in a future round.

Kind regards,
Admissions Team, [Course Name]

Candidate: Anna Svensson
Scores: Technical 5/5 | Motivation 4/5 | Learning potential 5/5 | Fit 4/5
Total: 18/20
Decision: ACCEPTED
Internal note (staff only): Strong computer science background and real React/Node.js project experience, with a clear goal of deepening backend skills. Not borderline.

Email:
Subject: Congratulations, you have been accepted to the Fullstack course

Dear Anna,

Congratulations! We are pleased to offer you a place on our Fullstack course.

Your computer science background and the web applications you have built with React and Node.js show a strong technical foundation. Your goal of deepening your backend skills fits the course well, and we think you will benefit from it and contribute a lot to the group.

To secure your place, please confirm your acceptance by [Confirmation Deadline] using [Next Steps Link]. Details about the schedule and onboarding will follow, ahead of the start on [Start Date].

We look forward to welcoming you.

Kind regards,
Admissions Team, [Course Name]
```

> Tip: Think about role, task, structure, and tone when writing your prompt.

---

## Exercise 2 — Meeting Notes to Clear Actions

### Scenario

A team had a meeting, but the notes are messy and unstructured.

The manager wants to quickly understand:

* what was discussed
* what decisions were made
* what the next steps are

---

### Example Input

```text
Project meeting - Monday

- talked about new website
- design not finished
- Johan working on API but waiting for access
- Sara finished UI
- deadline might move?
- issue with content from marketing
```

---

### Task

Write a prompt that:

1. Summarizes the meeting
2. Identifies decisions
3. Creates clear **action items**
4. Structures the output in a clean format

---

### Your Prompt

Write your full prompt below.

You can structure it as:

```text id="xw8p4s"
SYSTEM:
You are a meeting assistant who turns messy, unstructured notes into a
clear summary a busy manager can read in under a minute. You are accurate
and concise, and you never invent information.

RULES
1. Use ONLY information in the notes. Never invent names, owners,
   deadlines, decisions, or reasons.
2. Separate what is certain from what is uncertain:
   - A DECISION is something the notes say was agreed or decided.
   - Anything phrased as a question, a maybe, or a concern (for example
     "deadline might move?") is an OPEN QUESTION, not a decision.
   - If no decisions were made, write "No decisions recorded." Do not
     force one.
3. Action items must be concrete and start with a verb. Each one has:
   - Owner: the person named in the notes. If unclear, write "Unassigned".
   - Task: what needs to happen.
   - Due: the date if stated, otherwise "Not specified".
4. When you infer an action item from a blocker or open question rather
   than from an explicit statement, add "(suggested)" after it so the
   manager can tell it was inferred.
5. Mark blockers clearly. A blocker is anything that stops work from
   progressing (waiting for access, missing content, etc.).
6. Keep it short: one line per bullet, plain language, no filler.
7. Write in the same language as the notes.

OUTPUT FORMAT
Meeting: <title/day, or "Not specified">

Summary
<2-3 sentences: overall status of the project>

Progress
- <what is done or in progress, with who>

Decisions
- <decision> (or "No decisions recorded.")

Blockers and risks
- <blocker or risk, and what it affects>

Open questions
- <unresolved question>

Action items
| # | Owner | Task | Due |
|---|-------|------|-----|

Manager attention (max 2 bullets)
- <the most important things the manager should act on now>

USER:
Summarize the following meeting notes using the rules and output format.

[PASTE NOTES HERE]
```
```text
Expected output on the example input

Meeting: Project meeting, Monday

Summary
The new website project is partly complete. The UI is finished, but the design is not, and the API work is blocked by missing access. The deadline may be at risk.

Progress

Sara has finished the UI.
Johan is working on the API.
The design is not finished.

Decisions

No decisions recorded.

Blockers and risks

Johan is waiting for access, which blocks the API work.
Content from marketing is an issue, and the notes do not say what the problem is.
The deadline might move, and it is unclear by how much.

Open questions

Will the deadline move?
What is the issue with the marketing content?

Action items

#	Owner	Task	Due
1	Unassigned	Grant Johan the access he needs for the API (suggested)	Not specified
2	Unassigned	Clarify the content issue with marketing (suggested)	Not specified
3	Unassigned	Confirm whether the deadline will move (suggested)	Not specified
4	Unassigned	Finish the design (suggested)	Not specified

Manager attention

Johan's access is the clearest blocker, and resolving it unblocks the API work.
Decide on or confirm the deadline once the access and content issues are clear.
```

> Tip: Think about clarity, structure, and output format.

---

## Exercise 3 — Weekly Reports to Manager Overview

### Scenario

A team submits **weekly activity reports**.

Each report includes:

* completed tasks
* blockers
* time spent
* notes (often inconsistent)

The manager wants to:

* get a quick overview
* identify issues
* understand team progress

---

### Example Input

```text
Erik:
Worked on login bug, partially fixed.
Still issues with API.
About 6 hours debugging.
Blocked due to missing access.

---

Anna:
Finished dashboard UI.
Helped team with testing.
No blockers.
Worked ~8h/day.

---

Johan:
Started payment integration.
Not finished yet.
Unclear requirements.
```

---

### Task

Write a prompt that:

1. Summarizes each team member
2. Identifies blockers
3. Highlights risks
4. Creates a structured overview for the manager

---

### Your Prompt

Write your full prompt below.

You can structure it as:

```text
SYSTEM:
...

USER:
...
```

> Tip: Focus on extracting insights and structuring information clearly.

---
