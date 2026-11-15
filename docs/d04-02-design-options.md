# AI Home Automation, Starter System: Design Options Comparison

**Document:** d04-02 · **Step:** 4, Design · **Version:** 1.0
· **Last updated:** 2026-11-15 · **Status:** Decided
· **Owner:** Software Architect (Design chat)

## 1. The Decision

**Question:** How should the system turn spoken words at the front door into
actions: fully on the Raspberry Pi, through cloud speech and cloud AI, or with
an open-ended speech model on the Pi?

**Why it matters:** The voice setup ("voice pipeline") serves five of the nine
use cases (UC-3, UC-4, UC-5, UC-7, and UC-8, which sets the wake word). It
decides whether the spoken password stays on the Pi, whether voice commands meet
the 3-second target, the monthly cost, and whether a cloud voice service is part
of the system at all. Changing it after Step 7 would mean rewriting the voice
tests and the build guide.

**PRD source:** d03-01 v1.1: Section 3 (Users: Household member, Owner, Cloud
voice service), Section 5 (UC-3 to UC-5, UC-7, UC-8), Section 6 (Speed: voice
commands within 3 seconds; Privacy and data), Section 7 (budget; cloud AI
allowed; secrets on the home system only).

**Already decided (not options here):** the wake word is detected on the Pi,
because the USB speakerphone has no wake word of its own; the wake word comes
from the built-in list; the spoken password must stay on the Pi (all b0ts,
2026-11-14).

## 2. The Options

Every option uses the same front end: the USB speakerphone plugged into the Pi,
Home Assistant's "Assist Microphone" add-on to listen through it, and the
openWakeWord add-on to hear the wake word on the Pi. They differ in what
happens after the wake word.

| Option | Plain-language description |
|---|---|
| A: Phrases on the Pi | After the wake word, a small speech program on the Pi (Speech-to-Phrase) recognizes only a fixed list of phrases: the light commands, arm and disarm, and the password. Home Assistant's built-in command matching acts on them, and a voice program on the Pi (Piper) speaks the replies. Nothing leaves the house. |
| B: Cloud speech and Claude | After the wake word, the audio goes to Home Assistant Cloud (Nabu Casa) to become text, and Claude works out what was meant, so people can phrase things freely. For the password only, the system switches to Option A's on-Pi phrase recognition, so the password never leaves the Pi. |
| C: Open-ended speech on the Pi | After the wake word, a general speech model on the Pi (Whisper) turns any speech into text, and Home Assistant's built-in command matching acts on it. Nothing leaves the house, but it is slower. |

## 3. Side-by-Side Comparison

| Measure | Option A: Phrases on the Pi | Option B: Cloud speech and Claude | Option C: Open-ended speech on the Pi |
|---|---|---|---|
| Fits the users (PRD Section 3) | Yes for the household; commands must be said in the supported wording | Best: household members can phrase commands freely | Yes; any wording is transcribed, but commands must still match known sentences |
| Covers the Must-have use cases | All of UC-3 to UC-5, UC-7, UC-8 | All, but the password step needs a switch to on-Pi recognition mid-conversation (to verify in Step 6) | All, but likely misses the 3-second target |
| Speed (voice command within 3 seconds) | Strong: Home Assistant reports Speech-to-Phrase transcribes in about 150 milliseconds on a Pi 5 | Depends on the internet and cloud response time; the AI step adds delay (estimate: 1 to 3 seconds) | Weak: Home Assistant reports about 8 seconds per command on a Pi 4; a Pi 5 is faster but likely still over 3 seconds (estimate; to measure in Step 6) |
| Recognition accuracy (9 of 10 commands) | High for the fixed phrases; anything else is not understood | High for free wording; depends on the cloud service | Variable on a Pi |
| Password stays on the Pi | Yes | Only if the switch to on-Pi recognition works; otherwise no | Yes |
| Works with the internet down | Yes for voice (a bonus; the PRD doesn't require it) | No | Yes for voice |
| Spoken password risk | A phrase-only recognizer always picks the closest known phrase, so a wrong password could be heard as the right one. Mitigation: the password is a spoken code of digits, every digit combination is a known phrase, and Home Assistant compares the code with the stored one | Same as A for the password step | Low: it transcribes what was said |
| Estimated cost to build | Lowest: built-in add-ons and sentences written in YAML (estimate) | Highest: two voice setups plus switching between them (estimate) | Low to medium (estimate) |
| Estimated cost to run | $0 a month | About $6.50 a month for Home Assistant Cloud, plus Claude API use within the $10 limit (estimate) | $0 a month |
| Time to first working voice command | Shortest (estimate) | Longest (estimate) | Short, if the speed is acceptable (estimate) |
| Security and privacy | Best: no audio or text leaves the house | Audio after the wake word goes to Nabu Casa, and the text goes to Anthropic, as the PRD allows today | Best: no audio or text leaves the house |
| Fits the constraints (PRD Section 7) | Yes; leaves the PRD's "Cloud voice service" actor unused (needs a small PRD change) | Yes, as the PRD is written | Yes, but the speed requirement is at risk |
| How AI is used | AI helps build the system (Claude Code), not run it | AI understands commands while the system runs, like the reference system | AI helps build the system, not run it |

Sources: Home Assistant, "Speech-to-Phrase brings voice home – Voice chapter 9"
(2025-02-13) and "Set up a fully local voice assistant" (home-assistant.io), for
the speed figures; nabucasa.com FAQ, for the Home Assistant Cloud price.

## 4. Recommendation

**Recommended option:** A: Phrases on the Pi

**Why:** Every voice use case (UC-3 to UC-5, UC-7) uses a short, fixed set of
commands, which is exactly what Speech-to-Phrase is built for. It's the only
option that meets the 3-second target with room to spare and keeps the password
on the Pi without a tricky mid-conversation switch. It also matches b0ts's
stated preference for phrase detection on the Pi, and it costs nothing a month.

**What we give up:** People can't phrase commands freely ("lights out on the
porch" won't work unless that wording is added), and no AI understands commands
while the system runs, so the house has no AI personality like the reference
system's. That can be added later, in the planned on-premises AI project. The
PRD's "Cloud voice service" actor and its privacy wording about cloud audio
would also need a small change, through the Requirements chat.

**What would change the recommendation:** If free-form wording or an AI
personality becomes a Must have, Option B is better. If Speech-to-Phrase can't
recognize commands reliably through the speakerphone in the Step 6 test, fall
back to Option B for commands, keeping on-Pi recognition for the password.

## 5. Open Questions

- Does the Assist Microphone add-on play spoken replies and announcements (the
  exit-delay countdown, the alarm announcement every 5 minutes) through the USB
  speakerphone, or is a separate way to play sound needed? (DevOps, Step 6
  hardware check)
- Can Home Assistant keep listening for the password without a second wake
  word, or must the person say the wake word again before the code? (DevOps,
  Step 6; affects the UC-5 3a wording in the build guide)
- Is a spoken code of digits acceptable as "the password" in UC-5 and UC-7?
  Answered: yes (b0ts, 2026-11-15; Spec DD-6, PRD request R3).
- Which speakerphone model is it? Answered: Jabra Speak 510, model PHS002W
  (b0ts, 2026-11-15). Does it come with a USB Bluetooth dongle?
  Home Assistant OS's Bluetooth is meant for sensors rather than audio, so
  moving the speakerphone away from the Pi probably needs a dongle that appears
  to the Pi as a USB audio device. (b0ts; DevOps, Step 6)

## 6. Decision

| Chosen option | Decided by | Date | Spec Design Decision ID |
|---|---|---|---|
| A: Phrases on the Pi | b0ts | 2026-11-15 | DD-2 |
