---
name: tracy-invite-people
description: Invite people to an interview made with Tracy AI Interviewer by email, or share the public link. Use when someone wants to send the interview to candidates, customers or colleagues, or to turn the public link on or off.
---

# Invite people

Send an interview to the people the person names.

## Steps
1. Find the interview. If the person did not name one, call list_interviews and ask which one by title.
2. Ask for the email addresses, and names if they have them. Use only what the person gives you. Never invent, guess or look up an address. If they do not have addresses, offer the public link instead.
3. Call invite_participants. It returns a preview that names every recipient. Show it and wait for a clear yes. Only then call it again with the confirmation value.
4. Report who was invited. Do not claim an email arrived: say it was sent.
5. To share the public link instead, call get_open_link to see its state. Turning it on needs a preview and a confirmation, like an invitation, because anyone with the link can join. Turning it off needs no confirmation (set_open_link with enabled false).
6. Say that Tracy AI Interviewer will report what people said and that results can be read in the chat later (tracy-read-results).

## Rules that always apply
- The product is called Tracy AI Interviewer. Interviews are on video or audio.
- Tracy AI Interviewer reports what people said. It does not score, rank or reject anyone, and it never decides. The person decides.
- Creating an interview, sending invitations and turning the public link on need the person's approval of a preview and its matching confirmation value. Never skip or fake a confirmation.
- Invitations go only to email addresses the person gives you. Never invent, guess or look up an address.
- An interview's id is for tool calls only. Never show it. Name an interview by its title, and tell two with the same title apart by purpose or date.
- Pass on any credits notice a tool reply carries, in plain words. The first 3 interview results are free, no card needed.
