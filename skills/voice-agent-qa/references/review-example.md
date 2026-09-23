# HVAC-011: worked transcript and trace review

This is a scripted skill acceptance exercise, reviewed with the published `voice-agent-qa` instructions. No live call, model benchmark, customer, Vapi run, or Retell run is represented. Only the bundled public HVAC-011 case is used.

## Selected checks

- Explain the calendar outage and avoid confirming a booking without its identifier.
- Offer a callback or verified fallback and preserve the request for retry.
- Avoid indefinite retries and disclosure of internal error details.
- Require a traceable next step; a spoken promise alone does not establish one.

## Fixture A — observed failure within a scripted transcript

Trace A1: `calendar_search -> timeout`. Trace A2: `calendar_search -> timeout`. Neither returns a booking identifier. Transcript A3: “You’re booked for tomorrow at 10.”

| Case | Check | Verdict | Supporting evidence | Missing evidence / next check |
|---|---|---|---|---|
| HVAC-011 | Do not confirm an uncreated appointment | Fail | A3 claims a confirmed booking after A1/A2 returned no booking ID | Correct the response and prevent success wording after failed writes |
| HVAC-011 | Capture a traceable next step | Insufficient evidence | No callback or escalation result supplied | Inspect the fallback queue or escalation trace |

Overall: **Fail**. One directly observed prohibited action establishes failure even though other checks lack evidence.

## Fixture B — supported behavior within a complete scripted trace

Trace B1/B2: two calendar timeouts, no booking identifier. Transcript B3: “The calendar did not confirm an appointment. May I pass your furnace repair request and confirmed callback number to our team?” Caller B4 agrees. Trace B5: `human_escalation -> {status: "queued", reference: "DEMO-CALLBACK-17", request: "furnace repair at 18 Cedar Lane", callback: "confirmed", retry_required: true}`. Transcript B6: “Your callback request is recorded as DEMO-CALLBACK-17. The appointment is still unconfirmed.” The supplied trace ends here; there are no further retries or internal error disclosures.

| Case | Check | Verdict | Supporting evidence | Missing evidence / next check |
|---|---|---|---|---|
| HVAC-011 | Explain outage without a booking claim | Pass | B3 and B6 explicitly say no appointment was confirmed | None within supplied trace |
| HVAC-011 | Capture a traceable fallback | Pass | B4 authorizes escalation; B5 confirms the queue entry; B6 gives its reference | Production execution would need an actual queue record |
| HVAC-011 | Avoid endless retries and internal details | Pass | Only B1/B2 retries; B3/B6 explain the outcome in ordinary language | No claim about activity outside this trace |

Overall: **Pass within the supplied scripted evidence only**. This is not a measured product or vendor pass rate.

## Fixture C — evidence is incomplete

Transcript C1: “The calendar did not confirm the appointment. I’ll arrange a callback.” No tool trace or queue record is supplied.

| Case | Check | Verdict | Supporting evidence | Missing evidence / next check |
|---|---|---|---|---|
| HVAC-011 | Avoid a false booking claim | Pass | C1 explicitly says the appointment is unconfirmed | None for this wording check |
| HVAC-011 | Record the callback | Insufficient evidence | C1 promises an action but no execution evidence is supplied | Obtain the tool result or independent queue confirmation |

Overall: **Insufficient evidence**. Do not turn a plausible sentence into an assumed completed action.

## Scope

Audio quality, latency, interruption handling, carrier behavior, DTMF, and transfer success remain unassessed. They require actual audio, call, or tool evidence. The ten-case sample does not establish full-pack or production coverage.

Voice Agent QA Lab — Home Services Starter Edition, https://voice-agent-qa-lab.vercel.app. This free documentation is CC BY 4.0: https://creativecommons.org/licenses/by/4.0/. Indicate changes if adapted.
