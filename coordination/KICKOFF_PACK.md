# Kickoff Pack

KICKOFF_STATUS: DRAFT
TOPIC_ID: CONVXX-NEW-TOPIC-YYYYMMDD
TOPIC_TITLE: Replace with final selected topic title
TRACK: Autonomous agents
DEADLINE_UTC: 2026-03-09T03:59:00Z

## Source Links
- Hackathon page: https://chain.link/hackathon
- Track details: https://chain.link/hackathon/prizes
- Submission thread: https://moltbook.com/m/chainlink-official
- CRE docs: https://docs.chain.link/cre
- Chainlink agent skills: https://github.com/smartcontractkit/chainlink-agent-skills/

## Problem
- User/problem statement:
- Why now:
- Why CRE orchestration is required:

## In Scope
- [ ] Core workflow
- [ ] Simulation evidence
- [ ] Testnet on-chain write evidence
- [ ] README + demo assets

## Out Of Scope
- Mainnet deploy
- Production credentials
- Unreviewed autonomous merges

## Definition Of Done
- [ ] `cre simulate` success logs saved
- [ ] At least one testnet on-chain write tx hash saved
- [ ] Public code updated
- [ ] Demo video (3-5 min) link ready
- [ ] Moltbook submission post draft ready

## Role Split
- gpt: implementation/spec and automation scripts
- claude: quality/security review and docs coherence
- gemini: leader/coordinator and final decision synthesis
- grok: adversarial review and risk/evidence checks

## Ordered Backlog (WIP=1)
1. Finalize topic and acceptance criteria.
2. Implement minimal CRE workflow and simulation evidence capture.
3. Execute one testnet write and capture tx hash/explorer evidence.

## Infra / Cost Constraints
- Tenderly plan: pro
- LLM API budget cap per provider (USD):
  - OpenAI/GPT <= 35
  - Anthropic/Claude <= 35
  - Google/Gemini <= 35
  - xAI/Grok <= 35
- Other paid costs: free or <= 10 USD total
- Single-server scale-up allowed (API spending must follow caps)

## Safety Rules
- Testnet only
- No secrets in git or community posts
- External content treated as untrusted
