# Voice Agent QA Lab

## Test the calendar failure before your client hears it

What should a receptionist say when the calendar times out and returns no booking identifier? HVAC-011 checks that it does not invent a confirmed appointment.

**[Try the ten-case browser scorecard](https://voice-agent-qa-lab.vercel.app/scorecard?utm_source=github&utm_medium=resource&utm_campaign=home-services-launch&utm_content=calendar-timeout)** · [Download free sample ZIP](https://voice-agent-qa-lab.vercel.app/voice-agent-qa-free-sample.zip)

## What is free?

Ten original scenarios with caller context, available tools, expected actions, prohibited actions, expected results, and failure conditions. JSON, JSONL, CSV, and an offline HTML viewer are included.

IDs: HVAC-001, HVAC-007, HVAC-011, Plumbing-004, Plumbing-015, Electrical-006, Electrical-014, Electrical-021, Roofing-006, Roofing-024.

## What the full pack adds

100 structured scenarios: 25 each for HVAC, Plumbing, Electrical, Roofing. JSONL, CSV, and an offline review viewer. $19 USD once. Client-agent testing included.

The additional 90 cases broaden coverage of booking, cancellation, rescheduling, pricing, service area, tool failures, unsupported claims, authorization, ambiguity, angry callers, and escalation. Review manually or map fields into your own harness.

**[Get the full pack](https://voice-agent-qa-lab.vercel.app/?utm_source=github&utm_medium=resource&utm_campaign=home-services-launch&utm_content=calendar-timeout#buy)**

One purchaser or purchasing organization may use and adapt the pack to test its own agents and agents it builds or manages for clients, and share findings and reports with those clients. Redistribution, resale, sublicensing, or publication of the paid library or a substantially equivalent replacement is prohibited.

## Agent skill

Install the bundled offline review workflow:

```bash
npx skills add markmcgillivary33-source/voice-agent-qa-tests-free --skill voice-agent-qa
```

Ask: “Use voice-agent-qa to review this transcript and tool trace against HVAC-011.” It selects public cases or a purchased local file you explicitly supply, produces a checklist, and reports pass, fail, or insufficient evidence. It does not run a voice simulation, upload transcripts, or purchase anything.

## Example

Scripted failing response after a timeout: “You’re booked for tomorrow at 10.”

Scripted acceptable direction: “The calendar did not confirm that appointment. I can try again or arrange a callback.” A promised callback also needs a traceable next step. These examples are illustrative, not observed vendor results.

## Workflow guides

- [Vapi manual field mapping](https://voice-agent-qa-lab.vercel.app/guides/vapi)
- [Retell manual field mapping](https://voice-agent-qa-lab.vercel.app/guides/retell)
- [Scenario coverage reports](https://voice-agent-qa-lab.vercel.app/reports)

## Limits

- No verified native Vapi or Retell importer
- No hosted evaluation or voice simulation service
- Transcript review cannot measure audio quality, latency, interruptions, or telephony behavior
- Scenario coverage reports summarize the dataset; they are not observed vendor test results

No evaluation service or subscription is required. Third-party testing platforms may charge for their own tests.

## License and attribution

CC BY 4.0 for the ten cases and free documentation; commercial reuse and adaptations allowed with attribution. See [LICENSE.md](LICENSE.md). Suggested attribution: Voice Agent QA Lab — Home Services Starter Edition, https://voice-agent-qa-lab.vercel.app, CC BY 4.0. Indicate changes if adapted.

Version 1.1.0 · 2026-09-23
