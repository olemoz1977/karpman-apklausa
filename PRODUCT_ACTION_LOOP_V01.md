# Drama Triangle — Reflection → Action → Return pilot v0.1

Status: PRODUCT PILOT SPEC
Date: 2026-08-25
Scope: LT-first pilot; current public LT/EN tool remains unchanged until the pilot is manually reviewed.

## Product hypothesis

A reflection tool is more useful when it does not stop at a result. After the result, 2rasi can quietly ask whether the person wants to try one small behaviour change, remember that self-chosen experiment locally, and help the person return to it later.

Core loop:

`Notice → Reflect → Choose → Experiment → Return → Notice again`

This is not a task manager, coaching diagnosis, habit streak, or behavioural prescription.

## Why Drama Triangle first

Conflict-role reflection naturally points toward an observable next interaction. A person can test one small change in a real conversation without needing a long development plan.

The action layer must not infer what the person "should" change from the highest score. The current scoring is an exploratory response map, not a validated diagnostic or recommendation engine.

## Methodological boundary

Original Karpman Drama Triangle roles are Victim, Rescuer, and Persecutor.

Creator, Coach, and Challenger are alternative roles from David Emerald's The Empowerment Dynamic (TED*), not original Karpman roles. The pilot must state this provenance clearly instead of presenting the mapping as part of Karpman's original model.

The pilot uses these exit directions as optional reflection language only. The user chooses what resonates.

## Pilot flow

### 1. Existing reflection
- 18 statements.
- Same current response/scoring logic.
- Result remains a browser-local response map.
- Percentage display is explicitly described as a transformation of the response average, not a normed psychological score.

### 2. Exit directions
Show three optional, non-prescriptive directions:
- More choice / Creator direction.
- More questions and boundaries / Coach direction.
- More clear, respectful challenge / Challenger direction.

Do not automatically select, rank, or recommend a direction from the score.

### 3. Intent question
Ask only after the result:

`Ar skaitant rezultatą kilo mintis, ką vienoje realioje situacijoje norėtum pabandyti kitaip?`

Choices:
- Taip.
- Dar nežinau.
- Ne dabar.

"Dar nežinau" and "Ne dabar" are valid endings. No pressure or negative wording.

### 4. Choose a direction
If "Taip", the user explicitly chooses one of the three directions.

Each direction offers a small example but does not auto-fill a commitment until the user chooses it.

Example behaviours:
- Choice: `Kai pagaunu save galvojant „negaliu“, įvardysiu vieną dalyką, kurį galiu padaryti.`
- Questions/boundaries: `Prieš siūlydamas sprendimą, pirmiausia paklausiu, ką kitas žmogus pats nori daryti.`
- Respectful challenge: `Kalbėsiu apie konkretų elgesį ir jo poveikį, o ne apie žmogaus savybes.`

The user can edit or write their own one-sentence experiment.

### 5. Reminder horizon
Offer only:
- 3 days
- 7 days
- 14 days

This is deliberately smaller than a full planner.

### 6. Local save
Store the experiment only in localStorage on the current browser/device.

Do not send experiment text to a server in v0.1.

Suggested local model:

```json
{
  "version": 1,
  "createdAt": "ISO-8601",
  "dueAt": "ISO-8601",
  "direction": "choice|boundaries|challenge",
  "experiment": "user text",
  "reminderDays": 7,
  "status": "open|done|partial|not_done|closed",
  "followUps": []
}
```

### 7. Calendar support
Allow download of an `.ics` reminder.

Privacy rule:
- event title is generic: `2rasi · grįžti prie eksperimento`;
- do not put the user's experiment text into the calendar event by default;
- event description says to return to 2rasi;
- event URL points to the pilot page / future live Drama Triangle page.

### 8. Return / follow-up
If a saved experiment exists, show it on return.

Ask:
`Kas nutiko?`

Choices:
- Pabandžiau.
- Iš dalies.
- Nepabandžiau.
- Nebeaktualu.

Then optional local text:
`Ką pastebėjai?`

No "failed", streaks, points, guilt, or gamification.

After completion, allow a new experiment. Do not automatically create recurring reminders.

## Privacy

- Test answers, result, experiment text and follow-up notes stay local in v0.1.
- No account required.
- No email required.
- Calendar export is initiated by the user.
- Clearing test answers must not silently delete a saved experiment; experiment deletion is a separate explicit action.

## Product measurement — next gate, not in local pilot

The local pilot is for UX validation first.

Before public promotion, add aggregate-only product telemetry or another explicit measurement path. Do not collect experiment text.

Useful aggregate events:
- result_view
- intent_yes
- intent_unsure
- intent_no
- direction_selected
- experiment_saved
- calendar_downloaded
- followup_completed

Possible dimensions:
- language
- selected direction
- reminder horizon

Do not create a psychological profile or persistent cross-tool identity from these events.

## Evidence questions

The pilot should answer:
1. Does the intent question feel natural after the result?
2. Can the user formulate one observable experiment without coaching assistance?
3. Is local save + calendar enough support before an app exists?
4. Does the return screen feel useful rather than nagging?
5. Does the product remain a reflection tool rather than becoming a task manager?

## Promotion gate

Do not replace the current public LT tool until:
- owner completes the whole pilot flow on mobile;
- experiment survives refresh/reopen;
- ICS imports correctly;
- follow-up can be completed and cleared;
- no existing test/scoring/export behaviour is broken.

EN adaptation comes after the LT interaction is accepted, not in parallel.
