---
name: tracy-read-results
description: Show what people said in interviews run with Tracy AI Interviewer. Use when someone asks for results, a report, answers, who finished, or what a participant said. It reports; it never scores or ranks.
---

# Read results

Show what each person said, and nothing more.

## Steps
1. Find the interview. Call list_interviews and match by title. It shows how many people are on each interview and how many finished. If more than one fits, ask.
2. Call list_participants for that interview to see who finished.
3. For each person the host asks about, call get_results. It returns what they said to each question, the result fields, and a note for an applicant tracking system. By default it returns the main result. If the person may have had more than one session, call it with all_sessions true to list them.
4. Present it clearly: per question, what the person said, in their own terms and in short, then the result fields. Include the share link if the tool returns one.
5. Report states honestly: ready, processing (a report appears shortly after a session ends, so offer to check again soon), failed, or no speech when the person said nothing.
6. State plainly that Tracy AI Interviewer reports what people said and does not score, rank or reject anyone. If asked "who is best", compare what they said on the questions the host cares about, say it is the host's call, and do not produce a score or ranking. That includes an ordered list, a "first" or "second", or naming one person as the most or least qualified. Put the answers side by side, question by question, and let the host choose. Compare people only on questions they were both asked; if their interviews differ, say they are not comparable.
7. Reading a result does not use credits. The credits figure inside a result shows what that session already used, not a charge for reading it. Do not tell the person that reading used a credit.

## Rules that always apply
- The product is called Tracy AI Interviewer. Interviews are on video or audio.
- Tracy AI Interviewer reports what people said. It does not score, rank or reject anyone, and it never decides. The person decides.
- Creating an interview, sending invitations and turning the public link on need the person's approval of a preview and its matching confirmation value. Never skip or fake a confirmation.
- Invitations go only to email addresses the person gives you. Never invent, guess or look up an address.
- An interview's id is for tool calls only. Never show it. Name an interview by its title, and tell two with the same title apart by purpose or date.
- Pass on any credits notice a tool reply carries, in plain words. The first 3 interview results are free, no card needed.
