# The Algorithm — v0.2.30 Release Notes

**Release date:** 2026-02-02
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.30

- **Agent Execution Pattern** — All Task calls must use run_in_background: true with polling. Foreground agents are banned. Polling pattern documented with 15-30 second update intervals.
- **Voice Notifications Non-Blocking** — Voice phase curl commands now use `&` suffix for fire-and-forget execution. Curl fires and returns immediately without waiting for voice server TTS/playback. Eliminates blocking during FULL responses.
- **Updated Never-Block Rule** — Strengthened with explicit ban on foreground agents. #1 cause of perceived stalls is foreground agent spawning.
- **Updated EXECUTE Phase Format** — BUILD/EXECUTE template now shows: spawn agents with run_in_background: true, poll agents, report progress every 15-30s, collect results when done.
- **Updated Common Failures** — Added: spawning foreground agents (no run_in_background), TaskOutput with timeout > 30s, not reporting agent progress.

## Key Sections Added

### Agent Execution Pattern (v0.2.30)

**The #1 cause of perceived stalls is foreground agent spawning.** Every Task() call MUST use `run_in_background: true`. There are ZERO exceptions.

#### The Pattern

```
1. Spawn agent in background:
   Task({
     subagent_type: "Engineer",
     prompt: "Investigate pipeline failure root cause",
     run_in_background: true
   })

2. Immediately tell user what was spawned

3. For long tasks (> 2min), periodically check:
   Every 30s: TaskOutput(task_id, block=false)
   Report progress

4. On completion:
   TaskOutput(task_id, block=true)
   Report final results
```

### Voice Notifications Non-Blocking

Voice phase curl commands now use `&` suffix for fire-and-forget execution:

```bash
curl -s -X POST http://localhost:8888/notify -H "Content-Type: application/json" \
  -d '{"voice_id":"...","message":"Entering the Observe phase"}' &
```

The `&` at the end means the command fires and returns immediately. The voice server handles TTS/playback asynchronously. Without `&`, each curl blocks text generation for 1-7 seconds.

### Updated Common Failures

- **Spawning foreground agents (no run_in_background)** — Foreground agents block the user interface. ALL non-fast agents MUST use background mode.
- **TaskOutput with timeout > 30s** — Never wait more than 30 seconds. Use polling with progress updates.
- **Not reporting agent progress** — After spawning background agents, actively poll and report status every 15-30 seconds.
