# System Design - shengji-app

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                        shengji-app                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌───────────────┐              ┌───────────────┐               │
│  │   backEnd     │─── DATA ────▶│  Processing   │               │
│  │   (INPUT)     │              │               │               │
│  └───────────────┘              └───────────────┘               │
│        │                                  │                      │
│        │                                  │                      │
│        ▼                                  ▼                      │
│  ┌───────────────┐              ┌───────────────┐               │
│  │   Health      │              │   Insights    │               │
│  │   Learning    │─────────────▶│   Analysis    │               │
│  │   Habits      │              │   Correlation │               │
│  │   Thinking    │              └───────────────┘               │
│  └───────────────┘                     │                         │
│         │                               │                         │
└─────────┼───────────────────────────────┼─────────────────────────┘
          │                               │
          │                               │
          ▼                               ▼
┌─────────────────────────────────────────────────────────────────┐
│  ┌───────────────┐              ┌───────────────┐               │
│  │  frontEnd     │◀─────────────│   Growth      │               │
│  │  (OUTPUT)     │              │   Loops       │               │
│  └───────────────┘              └───────────────┘               │
│        │                                                           │
│  ┌──────────────────────────────────────────────────────────┐    │
│  │  Distribution                                              │    │
│  │  ├─ x.md              - Technical thought leadership      │    │
│  │  ├─ instagram.md      - Marketing, personal brand        │    │
│  │  ├─ youtube.md        - Education, tutorials             │    │
│  │  └─ rednote.md        - Chinese market                   │    │
│  └──────────────────────────────────────────────────────────┘    │
│        │                                                           │
│  ┌──────────────────────────────────────────────────────────┐    │
│  │  Metrics                                                   │    │
│  │  ├─ engagement.json    - Likes, comments, shares, views  │    │
│  │  ├─ consistency.json   - Posting frequency, streaks      │    │
│  │  ├─ connections.md     - Meaningful connections          │    │
│  │  └─ ip-tracking.md     - Original ideas spread           │    │
│  └──────────────────────────────────────────────────────────┘    │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

## Data Flow

### Input Layer (backEnd/)
1. **Health** - Physical state data
2. **Learning** - Knowledge acquisition logs
3. **Habits** - Behavior tracking
4. **Thinking** - Internal reasoning, PRDs to self

### Processing Layer
1. **Pattern Recognition** - Correlate inputs with outputs
2. **Insight Generation** - Identify growth levers
3. **Content Strategy** - Optimize based on metrics

### Output Layer (frontEnd/)
1. **Distribution** - Multi-platform content publishing
2. **Metrics** - Quantifiable impact tracking
3. **Pipeline** - Content creation workflow

## Database Schema (backEnd/db/)

### schema.json
```json
{
  "health": {
    "exercise": {"date", "type", "duration", "intensity"},
    "sleep": {"date", "hours", "quality", "deep_sleep"},
    "body_metrics": {"date", "weight", "body_fat", "muscle_mass"}
  },
  "learning": {
    "reading": {"date", "title", "author", "pages", "notes"},
    "courses": {"date", "platform", "course", "progress"},
    "research": {"date", "topic", "sources", "findings"}
  },
  "habits": {
    "daily_routine": {"date", "habit", "completed", "streak"},
    "streaks": {"habit", "current_streak", "longest_streak", "total_days"}
  },
  "thinking": {
    "ideas": {"date", "content", "tags", "status"},
    "notes": {"date", "context", "content"},
    "specs": {"date", "title", "status", "metrics"}
  }
}
```

### metrics-history.json
```json
{
  "date": "YYYY-MM-DD",
  "health_score": 0-100,
  "learning_score": 0-100,
  "habit_score": 0-100,
  "thinking_score": 0-100,
  "output_score": 0-100,
  "overall_growth": 0-100
}
```

## Agent Integration Design

### Future Agents

1. **Growth Monitor Agent**
   - Input: `backEnd/db/export.json`, `frontEnd/metrics/*.json`
   - Output: Weekly growth report, improvement suggestions
   - Trigger: Weekly cron

2. **Social Media Agent**
   - Input: Platform APIs, `frontEnd/metrics/engagement.json`
   - Output: Auto-update metrics, trend analysis
   - Trigger: Daily cron

3. **Insight Agent**
   - Input: `backEnd/` + `frontEnd/metrics/`
   - Output: Correlations, best practices, content optimization
   - Trigger: On-demand

4. **Coaching Agent**
   - Input: All data sources
   - Output: Personalized growth guidance
   - Context: OpenCoach R&D platform

## API Design (Future)

```
GET  /api/export              # Export all data for agents
POST /api/health              # Log health data
POST /api/learning            # Log learning data
POST /api/metrics/engagement  # Update engagement metrics
GET  /api/insights            # Get AI-generated insights
```

## Security Considerations

- Personal data in `backEnd/` - keep private
- Public content only in `frontEnd/distribution/`
- API keys in environment variables
- Agent access via authentication tokens
