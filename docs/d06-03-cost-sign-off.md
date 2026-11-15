# AI Home Automation, Starter System: Cost Sign-Off Sheet

**Document:** d06-03 · **Step:** 6, Initial Infrastructure · **Version:** 1.0
· **Last updated:** 2026-11-15 · **Status:** Awaiting cost sign-off
· **Owner:** DevOps Engineer (Initial Infrastructure chat)

## 1. What Is Being Approved

**Option:** Self-hosted at home: Home Assistant OS on the Raspberry Pi 5
(Spec DD-1), reached from outside the home through Tailscale's free
Personal plan (Spec DD-3), with backups kept on storage the household
already owns.

**In one sentence:** The system runs on hardware already bought and owned,
so going live costs nothing more each month except the Claude Pro
subscription used for development. This sheet records the hardware total
(Tracking issue I4) against a one-time budget raised to $600 (pending
Tracking decision D15).

**Source:** Spec d04-01 v1.0, Sections 5.2 and 13 (DD-1, DD-3); the owner's
purchase lists (2026-11-15). The Infrastructure Options and Cost Analysis
(d06-02) isn't used for this: there is no hosting choice, because the PRD
fixes the platform (Tracking checklist, Next Action B).

## 2. Costs

All amounts are estimates in US dollars. Hardware is at listed prices plus
9% sales tax, rounded to the cent on each line. It was paid out of pocket,
with no receipts kept.

**Hardware (one-time, already bought):**

| Part | Store | Price | Tax (9%) | With tax |
|---|---|---|---|---|
| Raspberry Pi 5, 8 GB | Micro Center | $174.99 | $15.75 | $190.74 |
| CanaKit Pi 5 case with active cooler | Micro Center | $19.99 | $1.80 | $21.79 |
| Official Raspberry Pi 27 W USB-C power supply | Micro Center | $11.99 | $1.08 | $13.07 |
| SanDisk 1 TB Portable SSD (solid-state drive) | Micro Center | $129.99 | $11.70 | $141.69 |
| USB-A to USB-C cable, 1 m (3.2 ft) | Micro Center | $10.99 | $0.99 | $11.98 |
| SONOFF EFR32MG24 Zigbee USB coordinator | Amazon | $35.90 | $3.23 | $39.13 |
| Sengled Zigbee A19 bulbs, 4-pack | Amazon | $17.71 | $1.59 | $19.30 |
| SONOFF SNZB-03PR2 motion sensor | Amazon | $16.50 | $1.49 | $17.99 |
| Shelly BLU Door/Window ZB (SBDW-103C) | Micro Center | $22.99 | $2.07 | $25.06 |
| Shelly Plug US Gen4 | Micro Center | $24.99 | $2.25 | $27.24 |
| Raspberry Pi micro-HDMI to HDMI cable, 1 m | Micro Center | $7.99 | $0.72 | $8.71 |
| Jabra Speak 510 speakerphone | Already owned | $0.00 | $0.00 | $0.00 |
| USB extension and Ethernet cables | Already owned | $0.00 | $0.00 | $0.00 |
| **Hardware total** | | **$474.03** | **$42.67** | **$516.70** |

**Monthly:**

| Service | Expected per month | Source |
|---|---|---|
| Claude Pro (development, Steps 6 to 10) | $20.00 | Anthropic pricing, monthly billing, US |
| Claude API (application programming interface) credits | $0.00 expected; up to $10.00 allowed | Not needed at run time (D11); d02-01's allowance kept for development |
| Tailscale, Personal plan | $0.00 | Tailscale pricing page |
| Home Assistant OS and add-ons | $0.00 | Open source; Home Assistant Cloud not used (DD-3) |
| Backups to the owner's Mac, NAS (network storage drive) or external hard drive | $0.00 | Existing equipment |

**Summary:**

| Cost | Amount |
|---|---|
| Up-front | $516.70 spent. Up to $83.30 more, only if a hardware check shows a part is needed (for example, a powered USB hub or a Zigbee repeater) |
| Expected per month | $20.00 |
| First-year total | $756.70 ($516.70 + 12 × $20.00) |
| Three-year total | $1,236.70 ($516.70 + 36 × $20.00), assuming Claude Pro is kept for the whole time |
| Staff or volunteer time per month | Not counted (owner's choice) |

Electricity for the Pi isn't counted. It isn't part of the budget approved
in D4.

## 3. Spending Limit and Alerts

| Item | Value |
|---|---|
| Approved monthly limit | $50.00 (D4, unchanged) |
| Budget alert set at | Not needed: the only expected cost is the fixed $20 Claude Pro subscription, and no API credits are planned (owner's choice) |
| Alert goes to | b0ts (owner), if an alert is set later |
| If the limit is reached | Stop buying API credits and adding paid services; prepare a new version of this sheet |
| Approved one-time limit | $600.00 (pending D15; replaces D4's $500) |
| If the one-time limit would be passed | Don't buy the part; prepare a new version of this sheet first |

## 4. Who Pays

| Item | Value |
|---|---|
| Paid from | b0ts, personally (out of pocket) |
| Account owner | b0ts (owner): owns the Claude, Tailscale and Home Assistant accounts, and receives the bills and alerts |

## 5. Price Check

| Item | Value |
|---|---|
| Prices checked on | 2026-11-15 |
| Checked using | Hardware: the owner's purchase lists (listed prices; 9% tax added by DevOps). Claude Pro: [claude.com/pricing](https://claude.com/pricing) and the Claude help center ("What is the Pro plan?"). Tailscale: [tailscale.com/pricing](https://tailscale.com/pricing) |
| Based on | One home; one Pi; two household iPhones; two Tailscale users (the Personal plan allows up to 6 users, unlimited personal devices, non-commercial use only); no Home Assistant Cloud; backups to existing storage |

## 6. Review Again If

- Any hardware check (stages 1 to 3) shows that a part must be bought, such
  as a powered USB hub or a Zigbee repeater.
- A part must be replaced, for example the plug or motion sensor under the
  eaves (Spec DD-9, Spec Section 14).
- One-time spending would pass $600, or monthly spending would rise above
  the expected $20.
- Claude API credits are bought (set a spending alert then), or a paid
  service (such as Home Assistant Cloud) is considered.
- Tailscale's free Personal plan changes, or the household no longer fits
  in it.

## 7. Approval

| Approved by | Role | Date | Tracking Decision ID |
|---|---|---|---|
| b0ts | Owner and sole decision-maker | Pending | Pending (after D15) |

## 8. Change Log

| Version | Date | Change | Reason | Approved by |
|---|---|---|---|---|
| 1.0 | 2026-11-15 | First version | — | Pending |
