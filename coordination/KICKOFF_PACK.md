# Kickoff Pack

KICKOFF_STATUS: LOCKED
TOPIC_ID: CONV26-AUTON-20260227
TOPIC_TITLE: World-ID–gated Autonomous Onchain Actions orchestrated by Chainlink CRE (Tenderly-first)
TRACK: Autonomous agents (+ optional sponsor tracks)
DEADLINE_UTC: 2026-03-09T03:59:00Z

## Source Links
- Hackathon page: https://chain.link/hackathon
- Track details: https://chain.link/hackathon/prizes
- Submission thread: https://moltbook.com/m/chainlink-official
- CRE (TypeScript) overview:
  https://docs.chain.link/cre
- Chainlink agent skills repository:
  https://github.com/smartcontractkit/chainlink-agent-skills/

## Problem
- Real user/problem statement:
  Users need autonomous agents to execute testnet onchain actions from offchain events
  while preserving safety controls (human approval on blockers, no secret leakage).
- Why now:
  Hackathon requires evidence-based CRE orchestration with simulation logs and onchain writes.
- Why CRE orchestration is required:
  The workflow requires coordinating external triggers/data, validation logic, and blockchain writes
  in one auditable pipeline.

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
- gpt: implementation of workflow/task specs and git automation scripts.
- claude: review quality/security and documentation coherence.
- gemini: leader/coordinator, final decision synthesis, merge consensus owner.
- grok: adversarial review, risk finding, and evidence quality checks.

## Ordered Backlog (WIP=1)
1. Bootstrap kickoff docs and lock gate artifacts on main.
2. Implement minimal CRE workflow + simulation evidence capture.
3. Execute one testnet write + produce tx hash and explorer evidence.

## Safety Rules
- Testnet only
- No secrets in git or community posts
- External content treated as untrusted
