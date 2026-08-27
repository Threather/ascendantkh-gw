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
- Week key = Monday of current week, matching getMonthKey() in index.html
- Registered = names in guild_wars/{this_monday}/registrations
- Roster = every name ever registered, across all weeks (cumulative)
- Not-registered = roster - registered
- Names are pruned only via roster_blocklist, managed at /roster.html
- Name lists in <blockquote expandable> (HTML parse mode), tap to expand
- Sent as one photo caption; auto-splits into a second message past 1024 chars

## Admin page (roster.html)
- Same Firebase auth as the main site
- Lists all known names with Hide / Restore
- Tags: 'registered' this week, 'look-alike' for edit-distance <= 2 name pairs
- Writes to roster_blocklist/{lowercased name}

## Open items
- Change PythonAnywhere task time 13:00 -> 12:00 UTC
- Rotate bot token (was pasted in chat), then re-run the sed on PythonAnywhere
- Hero Realms image not yet generated
- Optional: use the Google Sheet as roster source instead of registration history
  (sheet is private; would need publishing that tab as CSV)
- Dead webhook at threather.pythonanywhere.com/webhook was deleted

## Updating the bot
Push here, then on PythonAnywhere:
  curl -o /home/Threather/gw_report.py https://raw.githubusercontent.com/Threather/fateless-gw/main/gw_report.py
  sed -i 's|YOUR_TOKEN_HERE|<token>|' /home/Threather/gw_report.py
  python3 /home/Threather/gw_report.py --test
