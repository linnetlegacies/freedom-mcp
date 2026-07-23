<!-- GENERATED — do not hand-edit. Source: linnetlegacies/freedom-ai scripts/generate-freedom-mcp-readme.ts -->
<!-- CATALOG-HASH:412eaef296e6a68d -->
# FreedomOS MCP server (`freedom-mcp`)

Connect Claude, Cursor, Codex, Grok Build, Windsurf — or any MCP client — to [FreedomOS](https://getfreedomos.com), the business operating system where AI agents run your company's day-to-day (finance, goals, customers, content, agent teams) while **anything that sends, spends, or hires asks you first**.

## Connect (about 2 minutes)

1. Sign up at [getfreedomos.com](https://getfreedomos.com), then create a personal key at [getfreedomos.com/mcp](https://getfreedomos.com/mcp) (shown once; revocable anytime).
2. Add the server:

```
Endpoint:  https://twuluxmoognlwtmaoqgo.supabase.co/functions/v1/freedom-mcp
Transport: streamable-http
Header:    Authorization: Bearer <your key>
```

**Claude Code (CLI):**
```bash
claude mcp add --transport http freedomos-eval https://twuluxmoognlwtmaoqgo.supabase.co/functions/v1/freedom-mcp --header "Authorization: Bearer <your key>"
```

**Claude Code (config file `~/.claude.json`, inside `mcpServers`):**
```json
"freedomos-eval": { "type": "http", "url": "https://twuluxmoognlwtmaoqgo.supabase.co/functions/v1/freedom-mcp", "headers": { "Authorization": "Bearer <your key>" } }
```

**Any other MCP client / `mcp-remote`:** point an HTTP MCP server at the endpoint with the same Authorization header.

Also listed on the [official MCP Registry](https://registry.modelcontextprotocol.io) as `com.getfreedomos/freedom-mcp`.

## Safety model

- Keys are per-user and tenant-scoped — a key only ever sees that user's own companies.
- Reads run freely. Writes are tiered; **sensitive/outbound actions mint an approval card** the human decides in FreedomOS — the agent cannot send, spend, or hire on its own.
- Revoking a key at [getfreedomos.com/mcp](https://getfreedomos.com/mcp) cuts access on the very next call.

## Tools (233)

### Advisors & scoring (ICP consult, deliberation, quality checks) (7)

| Tool | What it does | Tier |
|---|---|---|
| `challenge_as_customer` | Run your deliverable past the company's customer truth: REAL Customer Evidence first (when stored), then generated ICP as labeled simulation | read |
| `deliberate` | Run an adversarial deliberation on a decision | read |
| `derive_from_website` | SPIKE tool (.agent/design-docs/2026-07-09-magical-onboarding-buildout-mode.md, "The Assignment") | sensitive · approval-carded |
| `get_product_context` | Returns THIS company's product truth — the operator-authored offer + the SHIPPED, marketable capabilities (what the product does, and what i | read |
| `recalibrate_agent_jd` | Regenerate an agent's JD using fresh company context | sensitive · approval-carded |
| `resolve_brand_guide` | Draft a first brand guide (personality tone, visual/positioning dos and donts) EXTRACTED from the company's own canon documents, with a veri | sensitive · approval-carded |
| `synthesize_lead_hypothesis` | Given a lead journey (from query_lead_journey), produce a structured hypothesis: intent score, conversion-failure mode, suggested outreach a | write |

### Business data & workspace (finance, OKRs, customers, leads, content) (117)

| Tool | What it does | Tier |
|---|---|---|
| `add_customer_evidence` | Store one piece of REAL Customer Evidence for this company (paying-customer words/behavior, telemetry, review, operator-relayed quote, prosp | write |
| `add_lead` | Add a new lead to the Leads CRM (crm_leads) — the table the Leads tab, triage, and outreach all use | write |
| `analyze_team_needs` | Gather comprehensive team and company context for talent strategy analysis | read |
| `approve_pipeline_item` | Approve a content item for publishing — or REJECT it with approved:false | sensitive · approval-carded |
| `archive_pipeline` | Archive (or restore) a content pipeline — flips is_active off/on, mirroring the Content Pipeline UI's soft-delete/restore | write |
| `capture_idea` | Capture an idea into the user's Ideas | write |
| `clear_pipeline_learnings` | Reset all learnings for a pipeline and start fresh | write |
| `configure_dashboard` | Create or update a widget on your agent dashboard | write |
| `create_feature` | Add a new feature to the Feature Index | write |
| `create_folder` | Create a folder in the knowledge base for organizing files | write |
| `create_icp` | Create a NEW Ideal Customer Profile (ICP) from scratch and save it — no Customer Hunter UI needed | write |
| `create_key_result` | Add a key result to an objective (the KR in OKR) | write |
| `create_objective` | Create a new objective (the O in OKR) | write |
| `create_pipeline` | Create a new content pipeline to automate content creation | write |
| `create_tactic` | Create a new growth tactic for the company | write |
| `deactivate_agent` | Deactivate (archive) an AI agent/specialist from the team | sensitive · approval-carded |
| `delete_icp` | Delete a saved Ideal Customer Profile (ICP) | sensitive · approval-carded |
| `delete_idea` | Delete an idea from Ideas | write |
| `delete_key_result` | Archive a key result (safe delete — recoverable, never hard-deleted) | write |
| `delete_knowledge` | Archive a knowledge file by slug (soft delete) | write |
| `delete_objective` | Archive an objective and its key results (safe delete — recoverable, never hard-deleted) | write |
| `delete_tactic` | Archive a tactic (safe delete - recoverable) | write |
| `generate_key_results` | Generate intelligent, context-aware key result suggestions for an objective | write |
| `generate_tactics` | Generate AND save 5 grounded growth tactics for a 4-F category, composed from the company mission/vision, OKRs, and ICP customer profile | write |
| `get_actuals_vs_budget` | Compare actual financial results to budget/projections | read |
| `get_agent_outcome_panel` | Per-agent "what did the compute buy" facts for the operator: trailing-14-day credits, runs (with self-maintenance share), human-accepted vs  | read |
| `get_artifacts` | Get saved artifacts for the company | read |
| `get_brand_guidelines` | Get the company's brand guidelines — name, tagline, colors (hex codes), typography, personality/tone, naming rules, and VISUAL + POSITIONING | read |
| `get_cash_position` | Get current cash and bank account balances | read |
| `get_check_telemetry` | Read recent quality-check telemetry for the current company | read |
| `get_company` | Get detailed company profile including mission, vision, and settings. | read |
| `get_credit_usage` | Check credit balance, usage history, and cost breakdown | read |
| `get_financial_summary` | Get P&L summary with revenue, expenses, and net income for the company | read |
| `get_freedom_target` | Get the user's freedom target (monthly income goal to quit day job), current FCF progress, estimated freedom date, and assumptions | read |
| `get_grain_policy` | Read the content-grain (wisdom-layer) publish policy for the current company | read |
| `get_icps` | Get saved Ideal Customer Profiles (ICPs) from Customer Hunter | read |
| `get_lead_pipeline_snapshot` | Aggregate counts of the Leads CRM (crm_leads) for the current company: active leads by temperature (warm/cold/…/unset) and lifecycle stage,  | read |
| `get_monthly_trends` | Get month-over-month financial trends | read |
| `get_my_channel_partner_link` | Get YOUR channel partner **student share link** (https://getfreedomos.com/start/{slug}) — the classroom start page (copy Claude prompt first | read |
| `get_my_channel_partner_starter_pack` | Get YOUR classroom starter pack for students: the public share URL (https://getfreedomos.com/start/{slug}) where they copy a one-paste Claud | read |
| `get_my_channel_partner_stats` | Get YOUR channel partner stats: student share URL (/start/slug), rev-share terms, and referral counts by status (pending/joined/activated/cr | read |
| `get_my_companies` | List the companies the current operator can act in (their FreedomOS portfolio), with the operator's role in each plus an `about` line (entit | read |
| `get_my_profile` | Get the current user's profile information including name, title, contact info, and personal details. | read |
| `get_next_priority` | Answer "What should I work on?" in two beats: it leads with the single most-actionable pending Command Center card the operator's rail featu | read |
| `get_okrs` | List objectives and key results for the company | read |
| `get_pending_approvals` | Get CONTENT PIPELINE outputs waiting for approval/publish (changelogs, newsletters, social drafts) | read |
| `get_projections` | Get projected future values from financial forecasts | read |
| `get_reader_profile` | Get a team member's READER PROFILE — their per-domain expertise (novice/fluent/expert) that tells agents how to pitch internal cards, summar | read |
| `get_routing_overview` | See how agent output is currently routed — who is responsible for which domains in the company. | read |
| `get_tactics` | List tactics for the company | read |
| `get_team_members` | Get all team members for the current company | read |
| `get_team_roster` | Get complete AI team roster with roles, specialties, and capacity info | read |
| `get_transactions` | List company transactions with optional filters | read |
| `get_voice_profile` | Get the company's VOICE PROFILE — the operator's real writing voice the drafting agents ground on (style descriptor, in-voice DOs, out-of-vo | read |
| `grant_agent_tool` | Grant ONE specific tool to an agent's loadout (tool_access) | sensitive · approval-carded |
| `hire_agent` | DEPRECATED: Redirects to interview_for_hire | sensitive · approval-carded |
| `hire_agent_with_context` | Hire a new specialist with full hiring context gathered from the interview | sensitive · approval-carded |
| `ingest_voice_corpus` | Build or refresh the company's voice profile from REAL writing | sensitive · approval-carded |
| `interview_for_hire` | Research the company and return everything needed to propose a specialist hire in ONE shot | sensitive · approval-carded |
| `link_agent_okrs` | Link an agent to one or more company OKRs | write |
| `list_customer_evidence` | List ranked REAL Customer Evidence for this company (paying > telemetry > review > relayed > agent_as_user > prospect) | read |
| `list_dashboard_widgets` | List all dashboard widgets for a specific agent | read |
| `list_deals` | List CRM deals for the current company | read |
| `list_features` | List all product features in the Feature Index | read |
| `list_inbox` | List pending ideas in the user's Ideas | read |
| `list_knowledge` | List all knowledge files and folders saved for this company | read |
| `list_pipeline_learnings` | Show the style guide and recent revision history for a content pipeline | read |
| `list_pipelines` | List all content pipelines (changelogs, team updates, reports, customer newsletters, social posts) | read |
| `list_scheduled_reports` | List all scheduled reports for this company, optionally filtered by agent | read |
| `list_segments` | List the live lead segment tags for the current company with server-computed lead counts (excluding do-not-contact, archived, and test leads | read |
| `list_shared_with_me` | List all knowledge files and folders that have been shared with the current user | read |
| `list_workspace_ideas` | List ideas that have been assigned to this workspace | read |
| `manage_responsibilities` | Assign, delegate, or revoke responsibility domains for team members | write |
| `propose_work` | Create a new shared work-graph item (lab_work_items) so it is visible and coordinated across sessions and agents | write |
| `publish_pipeline_item` | Publish approved INTERNAL content to configured output | outbound · human-approved per send |
| `query_lead_journey` | Reconstruct the full journey of a lead — what they did on the site, what they signaled, what we have already sent them | read |
| `read_knowledge` | Read a Markdown knowledge file by slug | read |
| `reassign_reports` | Reassign all scheduled reports from one agent to another | write |
| `remove_dashboard_widget` | Remove a widget from an agent dashboard. | write |
| `request_content_revision` | Request changes to a content item | write |
| `resolve_work` | Mark a shared work-graph item resolved — verified (default), published, or cancelled | sensitive · approval-carded |
| `retire_feature` | Archive (retire) a feature so it stops showing to readers and agents, or restore a previously retired one | write |
| `revoke_agent_tool` | Remove ONE specific tool from an agent's loadout (tool_access) | write |
| `save_artifact` | Save an artifact (screenshot, analysis, report) to the company archive | write |
| `save_knowledge` | Save a Markdown knowledge file | write |
| `search_conversations` | Search past conversations with the user | read |
| `search_transactions` | Search transactions by description | read |
| `segment_leads` | Organize, select, or clear a lead segment on the Leads tab by its exact source tag (e.g | read |
| `set_grain_policy` | Create or update the wisdom-layer publish policy for ONE content grain in the current company | sensitive · approval-carded |
| `set_offer` | Author or update the company's grand slam OFFER — the operator-authored positioning agents ground all outbound in (the offer half of the pro | sensitive · approval-carded |
| `share_knowledge` | Share a knowledge file or folder with a specific user | write |
| `submit_content_to_pipeline` | Submit manual content to a pipeline for transformation | write |
| `suggest_collaboration` | Create a cross-agent collaboration request | read |
| `suggest_next_hire` | Analyze team gaps and recommend hires or routing to existing agents | read |
| `triage_idea` | Assign an idea to one or more workspaces | write |
| `unshare_knowledge` | Revoke a user's access to a shared knowledge file or folder. | write |
| `update_agent` | Rename a team member or fix its role/title | write |
| `update_agent_avatar` | Generate or regenerate AI agent profile avatar(s) for a company's AI team | sensitive · approval-carded |
| `update_agent_skill` | Create or update a skill (process/procedure) for an agent | sensitive · approval-carded |
| `update_brand_guidelines` | Update specific fields of the company's brand guidelines (visual identity, naming, positioning) | write |
| `update_company` | Update company profile | sensitive · approval-carded |
| `update_feature` | Update fields on an existing Feature Index entry — title, description, category, solves, limits, or demo_url | write |
| `update_feature_status` | Mark a feature as ready for marketing | write |
| `update_finance_note` | Add or update a note on a P&L account row | write |
| `update_icp` | Update specific fields of a saved Ideal Customer Profile (ICP) | write |
| `update_key_result` | Update a key result | write |
| `update_knowledge_section` | Update a specific section of a knowledge file by its ## header | write |
| `update_lead` | Edit an existing lead in the Leads CRM (crm_leads): name, email, phone, location, do-not-contact flag/reason, lifecycle state (new/active/fl | write |
| `update_my_profile` | Update the current user's profile | write |
| `update_objective` | Update an existing objective's title, description, or year | write |
| `update_pipeline` | Update an existing content pipeline | write |
| `update_pipeline_style_guide` | Manually add a style rule to a pipeline | write |
| `update_projection` | Update projected values for specific accounts and months in the financial plan | write |
| `update_reader_profile` | Update a team member's reader profile — set their baseline level or per-domain expertise (novice/fluent/expert) so future internal cards and | write |
| `update_tactic` | Update an existing tactic | write |
| `update_transaction_note` | Add or update a note on a specific transaction | write |
| `update_voice_profile` | Update the company's voice profile | write |

### Files & documents (10)

| Tool | What it does | Tier |
|---|---|---|
| `append_to_sheet` | Append rows to a Google Spreadsheet. | write |
| `batch_update_spreadsheet` | Perform batch operations on a Google Spreadsheet (formatting, merging, etc.). | write |
| `create_google_doc` | Create a new Google Doc in the user's Freedom OS folder | write |
| `create_master_plan` | Initialize a new multi-step project with a persistent Master Plan artifact | write |
| `create_spreadsheet` | Create a new Google Spreadsheet with optional headers. | write |
| `list_google_drive_files` | List files in the user's Google Drive | read |
| `read_google_doc` | Read content from an existing Google Doc by its ID. | read |
| `read_sheet` | Read data from a Google Spreadsheet. | read |
| `update_google_doc` | Append new content to an existing Google Doc. | write |
| `update_sheet` | Update specific cells in a Google Spreadsheet. | write |

### Integrations (Google, Stripe, Meta, X, analytics, email) (53)

| Tool | What it does | Tier |
|---|---|---|
| `audit_brand_visibility` | Audit whether Freedom OS appears in AI-generated search results | read |
| `browse_url` | Browse a web page in a real browser and take a screenshot | sensitive · approval-carded |
| `check_my_inbox` | Check your own agent email inbox (receive-only) for messages sent to your @agents.getfreedomos.com address, and read them | sensitive · approval-carded |
| `create_meta_ad_draft` | Create a complete Meta (Facebook/Instagram) ad draft — campaign + ad set + creative + ad — ALL in PAUSED state, spending nothing | sensitive · approval-carded |
| `draft_tenet_from_signal` | Draft a company tenet (mission or vision) FROM the company's existing website, for the operator to ratify or edit — instead of asking them t | sensitive · approval-carded |
| `generate_carousel` | Render a multi-slide image carousel + a LinkedIn-PDF from structured slide copy | write |
| `generate_image_xai` | Generate or EDIT an image using xAI Imagine | sensitive · approval-carded |
| `generate_vector_image` | Generate a native SVG vector image using Recraft V4 Pro Vector | sensitive · approval-carded |
| `generate_video` | Generate a video clip using AI (xAI Imagine, 3 credits) | sensitive · approval-carded |
| `generate_video_veo` | Generate a high-fidelity cinematic video using Google Veo 3.1 (5 credits) | sensitive · approval-carded |
| `get_ads_performance` | Get Meta ads results: spend, impressions, clicks, CTR, CPC, CPM, reach, conversions (actions), cost per action, and purchase ROAS — at accou | read |
| `get_cac_strategy` | THE tool for any question about this company's CAC strategy or LTV:CAC ratio — e.g | read |
| `get_decision_ledger` | THE tool for what the Freedom Engine has DECIDED for this company — the audit feed of every autonomous decision: what it auto-ran, what it t | read |
| `get_page_performance` | Get per-page search performance from Google Search Console — which pages get the most clicks, impressions, and best positions | read |
| `get_release_ledger` | THE tool for "did this piece ship on this channel" — reads the cross-channel Release Ledger, the queryable truth for every confirmed send (X | read |
| `get_search_performance` | Get search performance data from Google Search Console — queries, clicks, impressions, CTR, and average position | read |
| `get_site_list` | List all verified sites/properties in Google Search Console | read |
| `get_sitemaps` | List all sitemaps submitted to Google Search Console for a property — shows submission status, indexing coverage, errors, and warnings | read |
| `get_stripe_metrics` | Get Stripe metrics including average/median LTV, MRR, churn rate, active subscriptions, and an AI-recommended CAC target derived from the co | read |
| `get_subscription_stats` | Get subscription statistics from Stripe — active, trialing, past-due, and canceled counts plus MRR and ARR | read |
| `get_top_customers` | Get top customers ranked by lifetime value (LTV) or revenue from Stripe | read |
| `get_x_post_metrics` | Get engagement metrics for a tweet on X (Twitter) | read |
| `get_xero_report` | Get a LIVE financial report straight from the company's connected Xero ledger: ProfitAndLoss, BalanceSheet, BankSummary, TrialBalance, or Ex | read |
| `inspect_url` | Inspect a URL in Google Search Console — check indexing status, crawl errors, mobile usability, and rich results | read |
| `invoke_integration` | Execute a tool on a connected MCP integration | outbound · human-approved per send |
| `list_ad_accounts` | List the Meta (Facebook/Instagram) ad accounts on this company's connection, with status, currency, lifetime spend, and spend cap | read |
| `list_ad_campaigns` | List campaigns in a Meta ad account: status, objective, budgets (major currency units), and schedule | read |
| `list_corpus_inventory` | List what content material this company already has (knowledge folders like book-1/canon, SME Expert rules, idea_inbox assigned to the works | read |
| `list_integrations` | List ALL connected external integrations — MCP servers, OAuth accounts (Google, X, ...), and direct integrations (Xero accounting, Stripe) — | read |
| `list_xero_bank_transactions` | List LIVE bank transactions from the company's connected Xero ledger (paged, 100 per page, newest first) | read |
| `list_xero_contacts` | List contacts (customers/suppliers) from the company's connected Xero ledger, optionally filtered by a search term (paged, 100 per page) | read |
| `originate_content_ideas` | Surface CONTENT IDEAS from the company's own corpus and land them in the content pool + cards (same owner as promote_corpus_to_content) | write |
| `posthog_hogql` | Run an arbitrary HogQL (SQL) query against PostHog data | read |
| `posthog_list_events` | List all event types tracked in PostHog, ordered by usage | read |
| `posthog_list_insights` | List existing saved insights in PostHog | read |
| `posthog_query_funnel` | Build and run a funnel analysis in PostHog | read |
| `posthog_query_trends` | Query event trends from PostHog (pageviews, signups, DAU, etc | read |
| `preview_meta_ad` | Get a facebook.com preview link for a drafted Meta ad, so the user can see exactly what it will look like before deciding to activate | read |
| `promote_corpus_to_content` | Mint the NEXT content angle(s) from the company's corpus into content_ideas + Command Center cards | write |
| `query_sme` | Query an external Subject Matter Expert (SME) AI for verified domain knowledge | read |
| `read_web_page` | Read a web page and return its content as clean markdown | sensitive · approval-carded |
| `remove_background` | Remove the background from an existing image, leaving the main subject isolated on a transparent background (PNG). | sensitive · approval-carded |
| `request_connector` | Request that the operator connect an external integration (MCP connector) so you can use its tools | sensitive · approval-carded |
| `search_ad_targeting` | Search Meta's ad-interest targeting catalog (returns interest ids + audience sizes) | read |
| `search_connector_registry` | Search the vetted connector registry for an external integration (MCP connector) you need but that is not yet connected | read |
| `send_email` | Send an outbound email via the company's Resend connection | outbound · human-approved per send |
| `send_slack_message` | Send a message to a Slack channel or direct message to a team member | outbound · human-approved per send |
| `set_cac_strategy` | Change this company's LTV:CAC strategy (the acquisition-spend posture): aggressive (2:1, early-stage growth), standard (3:1, recommended def | sensitive · approval-carded |
| `set_meta_ad_status` | Activate or pause a Meta campaign, ad set, or ad | outbound · human-approved per send |
| `set_revenue_channels` | Declare where this business makes money — stripe, xero, shopify, amazon, ebay, manual invoicing, "none_yet" (pre-revenue), or other (name it | sensitive · approval-carded |
| `sync_stripe_conversions` | Record won deals from the company's connected Stripe so lead→paid conversion becomes measurable | write |
| `update_meta_ad_budget` | Change the daily budget of a Meta ad set (account currency, major units; structural cap applies) | outbound · human-approved per send |
| `vectorize_image` | Convert an existing raster image (PNG, JPG, WebP) to SVG vector format using Recraft | sensitive · approval-carded |

### Meta & discovery (7)

| Tool | What it does | Tier |
|---|---|---|
| `attach_product_request_pr` | Attach an existing freedom-ai GitHub PR URL to a product request and **resolve it by construction** (card → approved, product_status=fixed,  | write |
| `claim_product_request_for_builder` | Mint a paste-ready Builder claim recipe for a FreedomOS product request so a host coding agent (Grok Build / Claude Code) with Harness + gst | write |
| `get_product_request_status` | Check status of a product request you previously filed with submit_product_request for your operator | read |
| `open_product_request_draft_pr` | Open a draft GitHub PR shell for an approved FreedomOS product request (work ticket branch, no auto-code) | write |
| `report_feedback` | Report an error, issue, observation, or suggestion you encountered during your work | write |
| `scan_product_signals` | Scan a company for product-system bugs and unlocks (failed/timed-out activity runs, blocked_on_you cards, open error agent_feedback) and ret | write |
| `submit_product_request` | File a bug report or feature request with the FreedomOS product team | write |

### Navigation (1)

| Tool | What it does | Tier |
|---|---|---|
| `list_my_work` | List shared work-graph items (lab_work_items) in the current company — the cross-session shared plan | read |

### Workflows & agents (hire, run, schedule, approve) (38)

| Tool | What it does | Tier |
|---|---|---|
| `ack_attention_directive` | Mark a pending attention directive as acked after the host session has taken the instruction | write |
| `add_agent_activity` | Add ONE activity to an agent's activity plan without regenerating the whole plan | sensitive · approval-carded |
| `add_commitment` | Track a personal commitment, deadline, birthday, appointment, or obligation | write |
| `append_cos_preference` | Append one durable speech/taste preference for THIS operator only (re-injected on their next voice session mint) | write |
| `cancel_attention_directive` | Cancel a pending attention directive (operator changed mind / wrong target) | write |
| `cancel_commitment` | Cancel a commitment without completing it — marks it cancelled | write |
| `complete_commitment` | Mark a commitment as completed | write |
| `confirm_mcp_approval` | Confirm a pending MCP capability approval by spoken (or chat) yes/no | write |
| `create_attention_directive` | Queue a short instruction for an external coding/builder session (Grok terminal, Claude Code, or future FreedomOS runtime) | write |
| `decide_command_center_item` | Approve or deny a Command Center card | sensitive · approval-carded |
| `derive_capability` | Scan the company's connected source code (its GitHub repo, via the Pulse connection in Smart Tools) and DRAFT a capability list — shipped FE | sensitive · approval-carded |
| `draft_outreach` | Produce two outreach draft variants (A/B) for a lead given an angle | write |
| `get_activity_health` | Audit all agent activities for staleness, business outcome alignment, and cross-agent overlap | read |
| `get_agent_performance` | Get detailed performance stats for a specific agent: run count, quality scores, approval/denial rates, error count, recent errors with conte | read |
| `get_attention_budget` | THE tool for the founder's attention budget — the operator-set ceiling on pending review cards before they are 'overloaded' (e.g | read |
| `get_command_center_item` | Read ONE Command Center card by id — full description, full deliverable content, and full context payload, in ANY status (pending, approved, | read |
| `get_command_center_items` | List Command Center cards for the company (pending by default; pass status_filter for approved/denied/snoozed/all) | read |
| `get_cos_preferences` | Read THIS operator's saved CoS speech/taste preferences (user-scoped) | read |
| `get_executive_landscape` | Get a cross-domain view of everything on the user's plate | read |
| `get_team_pulse` | Get a real-time snapshot of team output volume, pending approvals, and founder load | read |
| `list_attention_directives` | List pending attention directives for THIS operator (optionally filtered by target_session_id) | read |
| `list_attention_sessions` | List THIS operator's coding/builder sessions (status, goal, ask) | read |
| `list_commitments` | List the user's active commitments | read |
| `ratify_capability` | Persist the operator-CONFIRMED derived features (from derive_capability) into the product capability index as source='derived' | sensitive · approval-carded |
| `remove_agent_activity` | Retire ONE activity from an agent's plan | sensitive · approval-carded |
| `request_attention_spawn` | Request a NEW local coding session from voice/chat (tab spawn) | write |
| `run_quality_check` | Evaluate content or media against your ICP persona using Gemini 3.1 Pro vision | sensitive · approval-carded |
| `run_tactic` | Run a saved growth tactic NOW by dispatching it to its agent as a one-off background activity, then return immediately (the work lands as a  | sensitive · approval-carded |
| `send_lead_draft` | Send an approved outreach draft to its lead via the company's Resend connection, then mark the draft 'sent' | outbound · human-approved per send |
| `set_attention_budget` | Set the founder's attention budget — the maximum pending review cards before they are 'overloaded' (a whole number 1–100; default 7) — for a | sensitive · approval-carded |
| `set_cos_preferences` | Replace THIS operator's full CoS preference block (or clear with empty) | write |
| `share_commitment` | Share a commitment with your spouse or partner so they can see it too | write |
| `toggle_agent_schedule` | Pause or resume an agent's scheduled activities — the whole activity plan, or a single activity via activity_name | sensitive · approval-carded |
| `trigger_agent_activity` | Trigger a specific agent to run a specific activity immediately | sensitive · approval-carded |
| `unshare_commitment` | Stop sharing a commitment with someone | write |
| `update_agent_activity` | Edit ONE existing activity in an agent's plan — change its name, description, frequency, tools_used, deliverable, or completion_criteria | sensitive · approval-carded |
| `update_commitment` | Update fields of an existing commitment — title, domain, due date, consequence, or description | write |
| `upsert_attention_session` | Emit or update thin session telemetry for THIS operator (host coding agent self-announce) | write |

---
Docs-only repository — the server is hosted; this README is regenerated from the live tool registry on every tool-surface change. Product: [getfreedomos.com](https://getfreedomos.com) · Connect page: [getfreedomos.com/mcp](https://getfreedomos.com/mcp) · Machine-readable summary: [getfreedomos.com/llms.txt](https://getfreedomos.com/llms.txt)
