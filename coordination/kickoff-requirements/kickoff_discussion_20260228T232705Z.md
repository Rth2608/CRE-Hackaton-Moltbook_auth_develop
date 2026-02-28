# Kickoff Final Decision

**Topic ID:** CONV26-AUTON-20260227  
**Working Title:** World-ID-gated Autonomous Onchain Actions orchestrated by Chainlink CRE (Tenderly-first)  
**Selected Tracks:** Autonomous Agents, Identity  
**Consensus Status:** Reached (Agents fully aligned on the core topic)  

**Final Topic Definition:**  
A World ID-verified DAO admin arms a Chainlink CRE HTTP-trigger workflow that, upon receiving a webhook, passes a Tenderly simulation and autonomously mints a non-transferable 'VerifiedHuman' Badge NFT on Base Sepolia.

## Requirements Analysis

- **User/Problem Statement:** Autonomous agent workflows currently lack sybil-resistant human identity verification before executing onchain writes, leading to rampant automation abuse and bot manipulation.
- **Trigger:** A webhook receiving a World ID verification payload (HTTP-trigger).
- **Onchain Action:** Minting a non-transferable 'VerifiedHuman' Badge NFT to the verified user's address on the Base Sepolia testnet.
- **Measurable Value:** Establishes a verifiable, sybil-resistant gateway for autonomous agents to execute state-changing actions safely. Combines identity proofing with pre-execution simulation to prevent malicious or failing transactions, providing auditable evidence of workflow integrity.

## Pre-conditions

- **Contract State:** 'VerifiedHuman' Badge NFT smart contract is deployed on Base Sepolia testnet.
- **Funding:** Execution wallet is funded with sufficient Base Sepolia testnet ETH for gas.
- **Infrastructure:** Chainlink CRE workflow is configured with an active HTTP webhook trigger.
- **Safety Tooling:** Tenderly Pro account is active, configured, and integrated into the workflow path for simulation.
- **Identity:** World ID testnet developer application is registered and configured to send payloads to the CRE webhook.

## Basic Flow

1. **Trigger Reception:** The Chainlink CRE HTTP-trigger receives a webhook payload containing a World ID verification proof and a target wallet address.
2. **Payload Parsing:** The CRE workflow extracts the identity proof and the target EVM address from the incoming request.
3. **Identity Validation:** The workflow cryptographically verifies the World ID proof against the World ID developer API/testnet registry.
4. **Simulation Preparation:** Upon successful verification, the CRE workflow constructs an EVM transaction to mint the 'VerifiedHuman' NFT to the target address.
5. **Safety Gate (Tenderly):** The workflow submits the constructed transaction to Tenderly for execution simulation.
6. **Simulation Assessment:** The workflow parses the simulation response to ensure the transaction succeeds without reverts and stays within predefined gas limits.
7. **EVM Execution:** Upon passing the safety gate, the CRE workflow securely signs and broadcasts the transaction to the Base Sepolia testnet.
8. **Evidence Logging:** The system records the Tenderly simulation logs and the final Base Sepolia transaction hash for auditability.

## Exception Flows

1. **Invalid World ID Proof:**  
   *Condition:* The provided World ID proof fails validation.  
   *Mitigation:* The workflow immediately aborts, logs an "Identity Verification Failed" error, and no simulation or transaction is attempted.
2. **Malformed Webhook Payload:**  
   *Condition:* The incoming HTTP request lacks required fields (e.g., missing address or proof).  
   *Mitigation:* The webhook responds with a 400 Bad Request, logs the parsing error, and terminates the run.
3. **Tenderly Simulation Reverts:**  
   *Condition:* The Tenderly simulation indicates the mint transaction will fail (e.g., user already owns the non-transferable NFT).  
   *Mitigation:* The workflow halts execution at the safety gate, logs the revert reason, and prevents broadcasting the doomed transaction to the network.
4. **Gas Price Spike or Insufficient Funds:**  
   *Condition:* Base Sepolia testnet base fee exceeds the configured maximum, or the execution wallet lacks sufficient testnet ETH.  
   *Mitigation:* The workflow pauses or aborts with a specific "Resource Exhaustion" error, alerting the admin without attempting a severely underpriced transaction.
5. **RPC Endpoint Timeout/Failure:**  
   *Condition:* The connection to the Base Sepolia RPC or Tenderly API times out.  
   *Mitigation:* The workflow implements a bounded exponential backoff retry mechanism; if all retries fail, it logs an infrastructure failure and safely terminates.

## Post-conditions

- A non-transferable 'VerifiedHuman' NFT exists on Base Sepolia owned by the verified user's address.
- Verifiable proof of execution (Base Sepolia transaction hash) is captured and stored.
- Pre-execution simulation logs (from Tenderly) are saved as evidence of the safety gate.
- No mainnet assets or production credentials have been exposed or utilized.

## Acceptance Criteria

- [ ] `cre simulate` success logs are saved and auditable.
- [ ] At least one testnet on-chain write transaction hash (Base Sepolia) is successfully captured and saved.
- [ ] Public code repository is updated with the workflow configuration and simulation evidence.
- [ ] A 3-5 minute demo video link is ready, showcasing the end-to-end trigger, simulation, and minting process.
- [ ] Moltbook submission post draft is completed and ready for final review.

## Next Cycle Focus (Analysis Only)

Analyze CRE SDK HTTP trigger schema compatibility and EVM client multi-call capabilities against World ID testnet docs to finalize the offchain proxy versus onchain verification architecture. Focus on identifying potential data-type mismatches between World ID's JSON payload and CRE's schema requirements.

## References

- https://docs.chain.link/cre
- https://moltbook.com/m/chainlink-official
- https://langchain-ai.github.io/langgraph/
- https://chain.link/hackathon
- https://chain.link/hackathon/prizes
- https://github.com/smartcontractkit/chainlink-agent-skills/
