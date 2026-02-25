# shengji-app - Productise Yourself

> "Make PRD and specs to yourself first not to agent"

Personal growth abstraction system. Productise yourself → loop for growth → build personal IP → feed into OpenCoach startup.

## Architecture: Input → Processing → Output

```
backEnd (INPUT) → [Processing] → frontEnd (OUTPUT)
     ↓                                ↓
Internal growth              Quantifiable impact
- Health                      - Engagement
- Learning                    - Consistency
- Habits                      - Connections
- Thinking                    - IP produced
```

## File Structure

```
shengji-app/
├── README.md              # Philosophy, system design, usage
├── .gitkeep               # Keep empty folders tracked
├── docs/
│   └── system-design.md   # Architecture overview
├── frontEnd/              # OUTPUT - Published content + metrics
│   ├── distribution/      # Published content by platform
│   ├── metrics/           # Impact quantification
│   └── pipeline/          # Content creation workflow
└── backEnd/               # INPUT - Database of growth
    ├── health/
    ├── learning/
    ├── habits/
    ├── thinking/
    └── db/                # Structured data for agents
```

## Platform Strategy

| Platform | Role | Target | Content Type | Character |
|----------|------|--------|--------------|-----------|
| **X** | Technical thought leadership | VCs, AI founders | Product demos, building insights | AI Agent founder |
| **Instagram** | Marketing, personal brand | Future users | Fitness, selfies, lifestyle | Discipline |
| **YouTube** | Education | Non-CS "vibe coders" | Short videos: frontend, backend, JS/TS, Agents | Teacher (Feynman technique) |
| **Rednote** | Chinese market | Chinese audience | Translated mix of all above | Hybrid |

## Content Workflow

```
ideas.md → refining/ → -draft.md → .md → platform
```

1. Capture raw ideas in `frontEnd/pipeline/ideas.md`
2. Move to `refining/` for work-in-progress
3. Update platform-specific `-draft.md` files
4. Publish to main `.md` files when posted
5. Track metrics in `frontEnd/metrics/`

## Usage

### Daily
- Update `backEnd/` with inputs (health, learning, habits, thinking)
- Capture ideas in `frontEnd/pipeline/ideas.md`

### Weekly
- Review metrics in `frontEnd/metrics/`
- Refine content from ideas to drafts
- Publish to platforms

### Monthly
- Review growth patterns
- Adjust content strategy based on metrics
- Update personal PRDs in `backEnd/thinking/specs/`

## Agent Integration (Future)

JSON structure in `backEnd/db/` enables:
1. Growth monitoring agent - analyzes metrics, suggests improvements
2. Social media agent - monitors platform metrics automatically
3. Insight agent - correlates inputs with outputs
4. Coaching agent - guides growth (OpenCoach R&D)

## License

Personal use version. Future: ship general version for others.
