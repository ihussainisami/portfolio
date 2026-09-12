# Tenant Reference Verification & Follow-Up Automation

## The Problem

Before a lease gets signed, someone has to check the applicant's rental history. That usually means emailing a previous landlord and waiting for a reply.

In practice that reply often never comes. The landlord forgets, the email sits unread, or it lands in spam. There's no system reminding anyone to follow up, so the agent has to manually track who has responded and who hasn't, often across a dozen applicants at once. A move-in date gets closer while the reference is still sitting untouched in someone's inbox.

This isn't a technology problem on the surface. It's a follow-up problem. And follow-up is exactly the kind of task that quietly falls apart when it depends on a person remembering to do it.

## The Solution

I built an automation that handles the entire reference request lifecycle without anyone needing to track it manually.

An agent submits the applicant's details once. From there, the system takes over: it emails the previous landlord a short reference form, waits for a response, and if nothing comes back within 48 hours, it automatically sends a reminder and alerts the agent at the same time. A separate scheduled check runs quietly in the background as a safety net, so even if something in the main flow gets missed, no case is left unattended.

Every step updates a central tracking sheet, so the agent always has a single place to see the status of every applicant, without opening a single email thread.

## How It Works

**1. Intake**
The agent fills out a short form with the applicant's name, the previous landlord's email, their own contact, and the property address. This creates a tracked record and immediately emails the landlord a reference request with a link to a short feedback form.

**2. Landlord Response**
The landlord fills out five simple yes/no questions (on-time rent, property damage, notice given, would rent again, overall recommendation). Submitting it updates the same tracked record automatically, no manual entry required.

**3. Automatic Follow-Up**
If the landlord hasn't responded after 48 hours, the system sends them a reminder on its own and notifies the agent at the same time, so nobody is left wondering whether a reference is still pending.

**4. Backup Safety Check**
An hourly background check scans for any case that should have been followed up on but wasn't, catching edge cases the main flow might miss.

## Architecture

The system is built as three connected n8n workflows, communicating through a shared Google Sheet that acts as the single source of truth:

- **Intake Workflow** – form submission, record creation, landlord email
- **Landlord Response Workflow** – feedback form, record update
- **Backup Checker Workflow** – scheduled safety net for missed follow-ups

Keeping these as separate workflows, rather than one large one, makes each piece easier to test, debug, and maintain independently.

## Why This Matters

A missed reference check isn't just an inconvenience. It's how agents end up with tenants who have a history of late payments or property damage that nobody caught in time. The cost of one bad tenant almost always outweighs the five minutes it takes to chase a reference properly.

This system doesn't replace the agent's judgment. It just makes sure the reference request never quietly disappears into an inbox.

## Tech Stack

n8n, Google Sheets, Gmail/SMTP, native n8n Forms. No paid tools, no third-party form builders.

## Links

- [GitHub Repository](https://github.com/ihussainisami/tenant-reference-verification-automation)
- [Demo Video](https://drive.google.com/file/d/19qq3UpHk7mRaThNHkNqWGv2OMTE2qbTl/view?usp=sharing)
