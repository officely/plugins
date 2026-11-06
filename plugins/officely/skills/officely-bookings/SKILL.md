---
name: officely-bookings
description: Find availability and create, change, cancel, or check in to Officely bookings. Use for booking desks, rooms, and other resources for yourself, colleagues, or visitors, and for explaining a booking's status or refusal.
---

# Bookings

Read the [MCP workflow](../officely/references/mcp-workflow.md) before using live tools, unless it is already in context.

## Retrieve the relevant behavior

- [Booking desks and rooms](https://docs.officely.app/using/how-booking-works.md): availability, booking lifecycle, changes, and check-in.
- [Book for a colleague or visitor](https://docs.officely.app/using/book-for-others.md): who the booking is for and authority to act for them.
- [Work with dates and times](https://docs.officely.app/building/dates-times.md): interpreting workplace dates and preparing time values.
- [When you can't book](https://docs.officely.app/using/booking-refusals.md): interpreting refusals.
- [Join a waitlist](https://docs.officely.app/using/waitlists.md): alternatives when resources are full.

## Approach the task

Resolve the workplace, requested dates and times, resource preferences, and person the booking is for. Use the workplace's timezone and retrieve the time guidance before constructing unfamiliar time values. Resolve an existing booking before changing, cancelling, or checking it in.

For a new booking where any matching resource will do, such as "a desk on the third floor", submit it with a `selector` filter and let Officely pick a free one; there is no need to check availability first. When the person wants to choose, inspect availability for the requested window and treat it as evidence for choosing a resource. Claim a reservation only after the booking action succeeds. If the requested resource is unavailable, present suitable alternatives or a waitlist option without changing the user's plans implicitly.

Read the returned booking state and explain whether the result is confirmed, pending, or refused. For a change, inspect both the current booking and any pending request before reporting the effective result. Use [Booking rules](../officely-booking-rules/SKILL.md) when diagnosing policy or when the user requests a policy change; a booking refusal alone is not a request to change the rules.
