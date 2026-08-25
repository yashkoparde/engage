# Realtime Event Protocol Specification

## Channel Architecture
All events are broadcast over Supabase Realtime channels scoped to active Room Codes:
- `room:{room_code}` — Master channel for room state, active activity ID, and countdown timers.
- `confusion:{room_code}` — High-frequency aggregate confusion metrics channel.
- `typer:{room_code}` — High-speed keystroke velocity and progress broadcast.
