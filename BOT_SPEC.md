# Fateless Bot — Spec (WIP)

## Config
- Bot: Fateless-Reminder-Bot (@Threather_trust_bot), id 8195471464
- Group: Fateless, chat_id -1003652956919
- Admin DM: 924385557
- Site: https://threather.github.io/fateless-gw/
- Schedule: daily 12:00 UTC = 7PM Cambodia (UTC+7)
- Host: PythonAnywhere free tier, 1 daily task

## Events
- Guild Party — daily 7:00-7:10PM
- Hero Realms
- Test Your Skill
- Breaking Army
- Guild War (30v30)

## Images
| Event | File |
|---|---|
| Guild Party | assets/guild-party.png |
| Test Your Skill | assets/test-skill.png |
| Breaking Army | assets/breaking.png |
| Guild War | assets/gw-register.png |

## Daily baseline (every day)
- Guild Party 7:00-7:10PM
- Hero Realms - no fixed time slot, run anytime (Monday = weekly reset, flag it)
- GW block included every day:
  - Mon-Fri: registration view (registered / not-yet-registered counts + expandable name lists)
  - Sat-Sun: lineup view (total, roles [H/T/D], attack/defend split, jungle top/bot, reserves)

## Weekly schedule (main event per day)
- Mon — Hero Realms weekly reset highlighted. Image: guild-party.png
- Tue — Breaking Army 7:30-9:30PM. Image: breaking.png
- Wed — Test Your Skill 7:30-9:30PM. Image: test-skill.png
- Thu — Breaking Army 7:30-9:30PM. Image: breaking.png
- Fri — Test Your Skill 7:30-9:30PM. Image: test-skill.png
- Sat — Guild War 7:30-9:00PM. Image: gw-register.png
- Sun — Guild War 7:30-9:00PM. Image: gw-register.png

## GW registration block (appears in message)
- Reads guild_wars/{latest_date}/registrations
- Registered count + names
- Not-registered = roster - registered
- Roster = unique names across all dates, aged out after 4 weeks
- Blocklist node to permanently hide bad/typo names
- Name lists in <blockquote expandable> (HTML parse mode), tap to expand
- Caption limit 1024 chars -> may need photo + separate text message

## Open items
- Rotate bot token (exposed in chat)
- Hero Realms image not yet generated
- Dead webhook at threather.pythonanywhere.com/webhook was deleted
