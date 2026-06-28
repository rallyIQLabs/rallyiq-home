# PostHog post-wizard report

The wizard has completed a deep integration of your project. PostHog was already initialized via the HTML snippet in `index.html`. Six event captures were added to the bottom `<script>` block, covering every significant user interaction on the RallyIQ landing page: CTA clicks, demo section visibility, video playback, feature chip selections, and waitlist form submission (success and failure). `posthog.identify()` is called on successful signup, linking the user's email and role data to their PostHog profile.

| Event | Description | File |
|---|---|---|
| `get_access_clicked` | User clicked a 'Get access' CTA button (nav or inline) | `index.html` |
| `demo_section_viewed` | User scrolled far enough to view the demo section (top of conversion funnel) | `index.html` |
| `demo_video_played` | User played the demo video on the landing page | `index.html` |
| `feature_chip_selected` | User toggled a feature priority chip in the signup form | `index.html` |
| `waitlist_signup_submitted` | User successfully submitted the early access waitlist form | `index.html` |
| `waitlist_signup_failed` | An error occurred while submitting the early access waitlist form | `index.html` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- [Analytics basics (wizard) — Dashboard](https://us.posthog.com/project/489203/dashboard/1770427)
- [Total waitlist signups](https://us.posthog.com/project/489203/insights/jYJ71kQo)
- [Waitlist signups over time](https://us.posthog.com/project/489203/insights/beLk7bTB)
- [Signup conversion funnel](https://us.posthog.com/project/489203/insights/jJwEfaRH)
- [Demo engagement](https://us.posthog.com/project/489203/insights/nsqiWpZ2)
- [Feature chip interest breakdown](https://us.posthog.com/project/489203/insights/4suBZkJD)

## Verify before merging

- [ ] Run a full production build (the wizard only verified the files it touched) and fix any lint or type errors introduced by the generated code.
- [ ] Run the test suite — call sites that were rewritten or instrumented may need updated mocks or fixtures.
- [ ] Add the exact PostHog env var names (`PUBLIC_POSTHOG_KEY`, `PUBLIC_POSTHOG_HOST`) to `.env.example` and any monorepo/bootstrap scripts so collaborators know what to set.
- [ ] Confirm the returning-visitor path also calls `identify` — currently `posthog.identify()` is only called on fresh signup. If your app gains a login flow later, add `identify` there too.

### Agent skill

We've left an agent skill folder in your project. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.
