---
name: tracy-practice-run
description: Let the person take their own interview first with Tracy AI Interviewer, as a practice or test run, to see what their candidates or participants will go through. Use when someone asks to try it, test it, practice, run a mock interview, or interview me for a role.
---

# Practice run

The person interviews themselves, so no candidates and no email addresses are needed.

## Steps
1. Find out the role or topic. If it is missing, ask one short question and offer one example, such as a sales manager role. Say that a practice run is a result like any other and uses one of the account's interview results (the first 3 are free).
2. Draft the interview with the tracy-suggest-interview skill and show the draft. Ask about the integrity signals for a video interview.
3. When the person approves, create it with create_interview: show the preview it returns and wait for a clear yes before calling it again with the confirmation. Say afterwards that the public link starts on and nobody has been emailed.
4. Turn the public link off right away with set_open_link (enabled false, no confirmation needed), so nobody else can join.
5. Offer to invite the person's own address with invite_participants and self set to true. That uses the address their account signed up with, so they are not asked for it. The preview names the address, and they may give another address instead. The invitation still needs their confirmation. Invite nobody else.
6. The invite reply carries their personal link. Give it to them to open at once. Afterwards, offer to read the result with tracy-read-results.

## Rules that always apply
- The product is called Tracy AI Interviewer. Interviews are on video or audio.
- Tracy AI Interviewer reports what people said. It does not score, rank or reject anyone, and it never decides. The person decides.
- Creating an interview, sending invitations and turning the public link on need the person's approval of a preview and its matching confirmation value. Never skip or fake a confirmation.
- Invitations go only to email addresses the person gives you. Never invent, guess or look up an address.
- An interview's id is for tool calls only. Never show it. Name an interview by its title, and tell two with the same title apart by purpose or date.
- Pass on any credits notice a tool reply carries, in plain words. The first 3 interview results are free, no card needed.
