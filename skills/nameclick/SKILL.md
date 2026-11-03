---
name: nameclick
description: Find one person's work email, with their roles and company, through Nameclick by Sourcey. Use when the user wants to reach a specific person at work and gives their LinkedIn profile, email, GitHub login, or name and company.
---

# Find a work email

Nameclick returns a stored record of a person: who they are, their work email and whether it was checked to take mail, their roles and their company.

1. Resolve the person first. Use the identifier the user gave: a LinkedIn profile address is best, then an email or GitHub login, then a full name with their company or its domain. Never guess an employer; if the user gave only a name, ask where the person works.
2. Call `find_contact` with that identifier. It spends one lookup only when it shows a work email; a miss, a record with no email or an ambiguous identity costs nothing.
3. Show the person before the email: name, title and employer, so the user can tell it is the right person. Say whether the address was verified and when it was last seen.
4. To show someone found before, call `get_contact`. It is free.
5. When the person has a route of their own, such as a contact form or a published address, prefer it and say so.

Look up only the person the user asked about. Never look people up in bulk, build a list, or use a result for anything the person would not expect from their work. Anyone can ask to be removed at sourcey.com/nameclick/remove.
