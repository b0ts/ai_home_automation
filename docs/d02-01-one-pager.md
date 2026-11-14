# AI Home Automation, Starter System: One-Pager

**Document:** d02-01 · **Step:** 2, Feasibility · **Version:** 3.9
· **Last updated:** 2026-11-14 · **Status:** Awaiting decision
· **Owner:** Product Manager (Feasibility chat)

## 1. Problem

b0ts has no home automation system to learn on, or to build later artificial intelligence (AI) projects on. A friend's Raspberry Pi system shows what's possible, but nobody has written down a path that others can repeat.

## 2. Who Has It

- b0ts, the owner and builder, and the household coming and going
- Hobbyists who find the public repo and want to build the same system
- Users of the AI-assisted software development lifecycle (SDLC) workflow, which hasn't been tried on hardware yet

## 3. Proposed Solution

One project, with one finish line, that delivers these use cases, using cloud AI the way the friend's system does:

1. **Christmas lights:** a smart plug turns them on before dusk and off a couple of hours later, then on a couple of hours before sunrise and off at sunrise.
2. **Porch light:** turns on for 10 minutes when someone approaches the front door after dark (longer when turned on by voice).
3. **Voice light control:** spoken commands, such as "turn on the porch light," understood by AI.
4. **Leaving and returning:** saying "Leaving the house" or "Arm the system" arms the alarm after a 10-second countdown. Saying "Returning to the house" or "Disarm the system" disarms it if either household phone is home; if neither is, the system asks for a password, which is stored locally and kept out of the repo.
5. **Back-door alarm:** if the back door opens while armed, the speaker announces the alarm, and the Christmas-light plug and the porch light flash SOS in Morse code for 30 minutes, unless turned off by command.

A step-by-step guide in the public repo lets others build it, with any compatible Zigbee bulbs. A later project moves all AI on-premises, for security.

## 4. Why Now

Most of the hardware is already bought, the friend's system is a working example, and he's available for advice. A Raspberry Pi can now run small AI models, so this makes a good base for later projects.

## 5. Rough Cost and Effort

| Item | Estimate |
|---|---|
| People and time | 1 person (b0ts), with advice from the friend; no deadline. Hardware is assembled and sanity-tested first, in three stages (Raspberry Pi; Zigbee devices, including a short SOS test of the plug and a smart bulb; speakerphone), so building and testing can focus on the use cases |
| One-time money | Under $500: Raspberry Pi 5 kit and solid-state drive (SSD), Zigbee coordinator, motion sensor, 4 Zigbee smart bulbs, Shelly smart plug, a Shelly BLU Door/Window ZB sensor and a USB speakerphone (total TBD) |
| Already in place (not in budget) | A computer for development (b0ts uses a Mac laptop); a home router with Wi-Fi and internet; a keyboard, mouse and monitor for first-time setup; two smartphones with the Home Assistant app, used to detect who is home |
| Monthly money | Up to $50: Claude Pro for development ($20), Claude application programming interface (API) credits (up to $10), and optional cloud voice processing (about $6.50) |

## 6. Success Measures

| Goal | How success is measured | Target |
|---|---|---|
| Christmas lights | On and off at the scheduled times, over 2 weeks | 14 of 14 days, within 5 minutes |
| Porch light | After dark: on within 2 seconds of an approach, off after 10 minutes; in daylight: stays off; over 2 weeks | 95% of approaches; 0 daytime turn-ons |
| Voice light control | Spoken on/off commands carried out | 9 of 10 |
| Leaving and returning | Arms 10 seconds after the command; disarms only with a household phone home or the right password; a wrong password leaves it armed | 10 of 10 each; 5 of 5 wrong-password tests |
| Back-door alarm | When armed: spoken alert and SOS flashing for 30 minutes or until stopped by command; when disarmed: nothing | 5 of 5 each, starting within 5 seconds |
| Within budget | Receipts and monthly bills | Under $500 one-time; at most $50 a month |
| Others can repeat it | A second person follows the repo's guide, with no help from b0ts | A working system |

## 7. Risks and Unknowns

- **USB speakerphone:** others have run USB speakerphones with Home Assistant, but with setup trouble. If it doesn't work, source a voice puck.
- **A prototype, not a security system:** with one door sensor and no monitoring or notifications, the alarm is a prototype. It doesn't replace a professionally installed system with 24-hour monitoring. It can be expanded later with more sensors, alarms, plugs and lights for presence simulation, and notifications.
- **Keep sensitive data local:** the disarm password and the home/away state are stored only on the Raspberry Pi, never on the web or in the repo, where bad actors could reach them.
- **Other hardware:** the Shelly plug's Zigbee mode is reportedly rough (Wi-Fi is the fallback); SOS timing over Zigbee may be uneven. Any hardware that proves incompatible will be replaced.
- **TBD:** the hardware total; the friend's rules; a second person for the replication test.

## 8. Recommendation and Request

- **Recommendation:** Go to Requirements
- **Reason:** The use cases are small and well supported, and testing the hardware first takes the biggest unknowns out of the build.
- **Request:** b0ts approves the use cases, the $500 one-time and $50 monthly budgets, and permission to write the Product Requirements Document (PRD, Step 3).
