# HEARTBEAT.md - Hackathon Deadline Tracking

## Deadline Alert System

Check current time (Pacific timezone) and calculate time remaining until **1:30 PM PST, Sunday Feb 1, 2026**.

**Alert thresholds:**
- 6 hours remaining: "🚨 6h to deadline - status check needed"
- 3 hours remaining: "⚠️ 3h to deadline - final sprint"
- 1 hour remaining: "🔥 1h to deadline - wrap up NOW"
- 30 min remaining: "⏰ 30min - submission prep only"

**Each heartbeat:**
- Log current time in PST
- Calculate hours:minutes to deadline
- If past a threshold, alert once

Keep minimal. This runs frequently.
