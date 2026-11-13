# ai_home_automation: Tracking Checklist

**Document:** d01-01 · **Step:** 1, Tracking · **Last updated:** 2026-11-12
· **Overall status:** On track

## 1. Project Summary

| Item | Details |
|---|---|
| Project | ai_home_automation |
| Description | An AI-assisted home automation system for b0ts's own home, modeled on the Raspberry Pi and Home Assistant system a friend (James) built. It reproduces a minimal version of his setup, a Raspberry Pi 5 (8 GB) with a 1 TB solid-state drive (SSD), a Zigbee coordinator, a motion sensor, and smart bulbs, and also tests whether the AI-assisted software development lifecycle (SDLC) workflow works for hardware projects. |
| Sample or own project | Own project |
| Where files live | GitHub: https://github.com/b0ts/ai_home_automation (public); local: `~/projects/ai_home_automation`; Claude Project: "ai_home_automation". |
| Stakeholders | b0ts (owner and sole decision-maker). James built the original system and is available for advice; he is not a stakeholder. |
| Signs off each step | b0ts |
| Tracking level | Small: checklist only |
| Status reports | On request only, for b0ts |
| Deadlines | None. Expected to move quickly. |
| Constraints | Total budget under $500. Hardware: Raspberry Pi 5 (8 GB), 1 TB SSD, SONOFF EFR32MG24 Zigbee USB coordinator, SONOFF SNZB-03PR2 motion sensor, Sengled Zigbee A19 bulbs (4-pack), plus case, power supply and cables. Approach follows James's system: Home Assistant OS on the Pi, with Zigbee devices. Tools: Claude Project chats for Steps 2 to 5; Claude Code in the project folder for Steps 6 to 10. Covers hardware and software. |

## 2. Step Checklist

- [x] Step 1: Tracking: initialized 2026-11-12 (ongoing)
- [ ] Step 2: Feasibility
- [ ] Step 3: Requirements
- [ ] Step 4: Design
- [ ] Step 5: User Experience
- [ ] Step 6: Initial Infrastructure (DevOps support continues through Step 10)
  - [ ] Cost sign-off: Cost Sign-Off Sheet approved, before anything is set up
  - [ ] Final sign-off: System Infrastructure Document approved, before Step 7
- [ ] Step 7: Test Creation
- [ ] Step 8: Implementation
- [ ] Step 9: Release
  - [ ] Demo approval: stakeholders tried the software on the local environment, before anything moves to the live servers
  - [ ] Go/no-go: Release Readiness Review, after the move and the private pilot, before real users are invited
- [ ] Step 10: Maintenance

## 3. Status Table

Not used for this project.

## 4. Decision Log

| # | Date | Step | Decision | Decided by | Reason |
|---|---|---|---|---|---|
| D1 | 2026-11-12 | 1 Tracking | Tracking initialized: small project, checklist only; workflow's default tools (Claude Project chats for Steps 2 to 5, Claude Code for Steps 6 to 10); status reports on request | b0ts | Project set up; small, single-phase build, with later projects in their own repos |
| D2 | 2026-11-12 | 1 Tracking | Repo is public, under the MIT license (copyright Robert H. Bourbonnais) | b0ts | Chosen during project setup |
| D3 | 2026-11-12 | 1 Tracking | Background notes (project intent and the description of James's system) kept out of the public repo | b0ts | Privacy: the notes describe a friend's home system |

## 5. Issue Log

| ID | Date raised | Step | Description | Impact | Owner | Status |
|---|---|---|---|---|---|---|
| I1 | 2026-11-12 | 1 Tracking | The workflow's prompts and templates are written for software-only projects. This project also has a hardware side: buying and assembling devices, flashing the operating system, and pairing Zigbee devices. | Steps 4, 6, 7 and 8 must explicitly cover hardware: the parts list and wiring in the Spec, physical setup in the Infrastructure Document, and manual or on-device checks in the Test Plan. Lessons can feed back into the workflow repo. | b0ts | Open |
| I2 | 2026-11-12 | 6 Initial Infrastructure | Some hardware was ordered before the Step 6 cost sign-off. | The Cost Sign-Off Sheet (d06-03) should list hardware already bought against the $500 budget, as well as any remaining costs, such as subscriptions or cloud AI usage. | b0ts | Open |
| I3 | 2026-11-12 | 2 Feasibility | The repo is public, and the background notes describe a friend's home system. | Resolved by D3: the notes stay out of the repo and are attached to chats directly. Deliverables should describe James's system only in general terms. | b0ts | Resolved |

## 6. Open Questions

- Which parts of James's system are in scope for the minimal build: cloud AI conversation through Claude, the voice puck, the occupancy "brain", or lights and motion only? (b0ts, in Step 2: Feasibility)
- Will ongoing costs, such as a Nabu Casa cloud subscription or Claude API usage, count against the $500 budget? (b0ts, by Step 6 cost sign-off)

## 7. Next Action

- **Next chat:** Step 2: Feasibility. Open a new chat named `02-feasibility` in the "ai_home_automation" Claude Project.
- **Prompt:** `prompts/c02-feasibility-prompt.md`
- **Templates to fill in:** `docs/d02-01-one-pager.md` only. This is a small, self-funded project, so the feasibility study (d02-02), pitch summary (d02-03) and proposal (d02-04) aren't needed.
- **Give it:** `prompts/c02-feasibility-prompt.md`, `docs/d01-01-checklist.md`, `docs/d02-01-one-pager.md`, and b0ts's background notes file (kept outside the repo)
- **Waiting on:** nothing
