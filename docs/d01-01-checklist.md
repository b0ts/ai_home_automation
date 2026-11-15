# ai_home_automation: Tracking Checklist

**Document:** d01-01 · **Step:** 1, Tracking · **Last updated:** 2026-11-14
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
- [x] Step 2: Feasibility: approved 2026-11-14 (D4)
- [ ] Step 3: Requirements (v1.0 sent back for a small revision, D8)
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
| D4 | 2026-11-14 | 2 Feasibility | Go: one-pager (d02-01) version 3.9 approved, including its five use cases (Christmas lights, porch light, voice light control, leaving and returning, back-door alarm), a one-time budget under $500, and up to $50 a month. Its length (about 950 words, over the template's 400) is accepted. | b0ts | Use cases are small and well supported; testing the hardware first removes the biggest unknowns. Open items I4 to I6 carry into Requirements. |
| D5 | 2026-11-14 | 2 Feasibility | Feasibility study (d02-02), pitch summary (d02-03) and proposal (d02-04) not used; their blank templates removed from `docs/` | b0ts | Small, self-funded project with a single idea |
| D6 | 2026-11-14 | 3 Requirements | Two approved success measures (D4) changed, as set out in PRD v1.0 Section 7: "Others can repeat it" now means a complete build guide in the repo, not a second person's working build; the back-door alarm starts within 5 seconds after a 10-second entry delay, and also after 3 wrong passwords | b0ts | A second builder isn't needed for this project to be done; the entry delay lets a household member disarm |
| D7 | 2026-11-14 | 3 Requirements | Accepted as written in PRD v1.0: the 10-second entry delay with the speakerphone near the front door (see I7); the Christmas-light schedule runs all year; SOS flashing on the smart plug (see I8) | b0ts | Prototype; the bulb color changes with the season; revisit if trials show a problem |
| D8 | 2026-11-14 | 3 Requirements | Go back: PRD revised to version 1.1. The alarm announcement asks the person to call the household ("call us") without giving a number, and the remote-disarm phone number is removed from the stored secrets | b0ts | A person let in while the household is away will already have the number; nothing need be stored or announced |

## 5. Issue Log

| ID | Date raised | Step | Description | Impact | Owner | Status |
|---|---|---|---|---|---|---|
| I1 | 2026-11-12 | 1 Tracking | The workflow's prompts and templates are written for software-only projects. This project also has a hardware side: buying and assembling devices, flashing the operating system, and pairing Zigbee devices. | Steps 4, 6, 7 and 8 must explicitly cover hardware: the parts list and wiring in the Spec, physical setup in the Infrastructure Document, and manual or on-device checks in the Test Plan. Lessons can feed back into the workflow repo. | b0ts | Open |
| I2 | 2026-11-12 | 6 Initial Infrastructure | Some hardware was ordered before the Step 6 cost sign-off. | The Cost Sign-Off Sheet (d06-03) should list hardware already bought against the $500 budget, as well as any remaining costs, such as subscriptions or cloud AI usage. | b0ts | Open |
| I3 | 2026-11-12 | 2 Feasibility | The repo is public, and the background notes describe a friend's home system. | Resolved by D3: the notes stay out of the repo and are attached to chats directly. Deliverables should describe James's system only in general terms. | b0ts | Resolved |
| I4 | 2026-11-14 | 2 Feasibility | The one-pager's hardware total is still TBD, and the parts list has grown (Shelly plug, door sensor, USB speakerphone). | Must be confirmed under the $500 one-time budget; the Step 6 cost sign-off (d06-03) depends on it. | b0ts | Open |
| I5 | 2026-11-14 | 2 Feasibility | The planned door sensor (Shelly BLU Door/Window ZB) needs confirming as a Zigbee model; Shelly's BLU line is mostly Bluetooth. | If it isn't Zigbee, the Design (Step 4) must add Bluetooth support, or a different sensor is chosen. | b0ts | Open |
| I6 | 2026-11-14 | 2 Feasibility | The porch-light use case needs a motion sensor that can see the front door; the SONOFF SNZB-03PR2 may be indoor-only. | Requirements and Design must say where the sensor goes, and whether an outdoor-rated sensor is needed (and its cost, under I4). | b0ts | Open |
| I7 | 2026-11-14 | 3 Requirements | The 10-second entry delay may be too short to walk from the back door to the speakerphone near the front door and disarm, especially if passwords are needed. | Could cause false alarms in UC-5 and UC-6 trials. Accepted for now (D7); if trials fail, a go-back to Requirements (longer delay, pause during disarm, or a second speaker). | b0ts | Open |
| I8 | 2026-11-14 | 4 Design | Flashing SOS on the smart plug for up to 30 minutes switches its relay many times and may wear it out. | Accepted (D7): if the plug fails, replace it and change how the alarm is shown. Design should note the plug's switching limits. | b0ts | Open |

## 6. Open Questions

- Does the Claude Pro subscription ($20 a month, used for development) count against the $50 monthly budget, or is it an existing cost? (b0ts, by Step 6 cost sign-off)
- What is the hardware total? (b0ts, see I4)

## 7. Next Action

- **Next chat:** Step 3: Requirements, back in the existing `03-requirements` chat, for PRD version 1.1 (go-back, D8)
- **Prompt:** `prompts/c03-requirements-prompt.md` (already loaded in that chat)
- **Templates to fill in:** `docs/d03-01-prd.md` (revise in place; add a Change Log row)
- **Give it:** the change in D8: the alarm says "call us" with no phone number, and the remote-disarm phone number is removed from the stored secrets (UC-6, UC-8, Section 3 Users, Section 6 Privacy). Decisions D6 and D7 for its Change Log
- **Waiting on:** nothing. After v1.1, return here for the go/no-go review; then Step 4: Design
