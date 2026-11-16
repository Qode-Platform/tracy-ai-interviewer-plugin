---
name: tracy-suggest-interview
description: Draft an AI video or audio interview with Tracy AI Interviewer from who the person wants to interview and what they want to learn. Use when someone wants to screen candidates, research customers or users, check references, check in with employees, set up an interview, or asks what Tracy AI Interviewer can do. It saves nothing and invites nobody.
---

# Suggest an interview

Turn "who I want to interview and what I want to learn" into a draft the person can review.

## Steps
1. Find out two things. Who will be interviewed (for example candidates for a senior backend engineer role, customers who cancelled last month, a designer's references). What the person wants to learn. If either is missing, ask one short question and offer one example. Never invent a role or a company.
2. Note anything else that matters: extra context such as the company or tone, the language (English, German, Spanish, French, Indonesian, Japanese, Korean, Dutch or Vietnamese; English if not said), and the format (video, or audio when people only have a microphone; video if not said).
3. Call the suggest_interview tool with that. It writes an unsaved draft.
4. Show the person the whole draft: the title, every question and every result field. Do not summarise it away.
5. For a video interview, explain the integrity signals in one sentence (a full-screen window, a face on camera and a pop-up if the face leaves the frame; Tracy AI Interviewer only reports) and ask whether to keep them on or turn them off. An audio interview has none.
6. Wait. Apply the person's changes by calling suggest_interview again and keeping the questions they liked. When they approve, ask if they want it created, and then create it as the next step: call create_interview, show the preview it returns, and wait for a clear yes before confirming. Never create anything the person has not approved.

Nothing is saved and nobody is invited until the person approves the draft and the preview.

## Rules that always apply
- The product is called Tracy AI Interviewer. Interviews are on video or audio.
- Tracy AI Interviewer reports what people said. It does not score, rank or reject anyone, and it never decides. The person decides.
- Creating an interview, sending invitations and turning the public link on need the person's approval of a preview and its matching confirmation value. Never skip or fake a confirmation.
- Invitations go only to email addresses the person gives you. Never invent, guess or look up an address.
- An interview's id is for tool calls only. Never show it. Name an interview by its title, and tell two with the same title apart by purpose or date.
- Pass on any credits notice a tool reply carries, in plain words. The first 3 interview results are free, no card needed.
