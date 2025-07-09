# Incident disclosure - 2025-06-12

## **Summary**

On **2025-06-12**, Cove identified and mitigated a reentrancy vulnerability in its farming rewards plugin contract derived from 1inch’s ERC20 Token Plugins. A timely white-hat operation secured **652,565 non-transferable COVE tokens**. No user funds were lost, and the vulnerability has been completely neutralized.

## **Impact**

* **Funds at Risk:** 652,565 non-transferable COVE tokens intended as rewards.  
* **Losses:** None (fully secured through prompt action).  
* **Affected Contract:** [CoveUSD–COVE Farming Plugin](https://etherscan.io/address/0xa74e0B738b053D9083451bBAB84c538ff2Cc701d).

## **Vulnerability Details**

The flaw involved reentrancy in the \_updateBalances function, lacking essential safeguards after [recent code optimizations](https://github.com/1inch/token-plugins/commit/3add2bd8f0c5d1e1090ae3fabb3cd8ca3b6d575b) by 1inch. Malicious plugins could exploit recursive callbacks, fraudulently inflating reward balances. The protective gas-limit check was removed inadvertently, reintroducing a known risk.

## **Mitigation & Fix**

* **Immediate Response:** Emergency halt via [stopFarming](https://etherscan.io/tx/0x...); subsequent [white-hat rescue](https://etherscan.io/tx/0x...127) secured vulnerable tokens.  
* **Permanent Fix:** The team is determining the safest way to resume the rewards program and will be airdropping the reclaimed COVE and rewards tokens to users. Further communication will follow in the coming weeks.

## **Timeline (UTC)**

* **2025-06-12 00:18** – Vulnerability reported via Immunefi by [**adriro (@adrianromero)**](https://x.com/adrianromero) from [yAudit (Electi Security)](https://x.com/electisec), previously audited Cove for [Boosties](https://github.com/Storm-Labs-Inc/cove-audits/blob/master/2024-03-30_yAudit_Boosties.pdf).  
* **2025-06-12 01:06** – Emergency stop executed ([tx link](https://etherscan.io/tx/0x...)).  
* **2025-06-12 04:06** – White-hat rescue executed ([tx link](https://etherscan.io/tx/0x...127)).  
* **2025-06-12 13:35** – Incident resolved; comprehensive reviews confirmed no other vulnerabilities.

## **References**

* [Vulnerable Contract](https://etherscan.io/address/0xa74e0B738b053D9083451bBAB84c538ff2Cc701d)

## **Acknowledgements**

* **Researcher:** @adrianromero (yAudit/Electi Security, via Immunefi, $15,000 USDC bounty)  
* **Auditors and Security Partners:** Zellic, Pashov Audit Group (Krum Pashov), pcaversaccio, Security Alliance’s SEAL 911, Taylor Monahan, samczsun, 0xc0ffeebabe, Anton Bukov, 1inch team, Robert Chen (OtterSec), Jazzy (Zellic), Josselin Feist, and numerous others  
* **Storm Labs team:** Mike Daly, John Lim, Sunil Srivatsa

## **Contract Addresses / Commits**

```
Vulnerable FarmingPlugin: [0xa74e0B738b053D9083451bBAB84c538ff2Cc701d](https://etherscan.io/address/0xa74e0B738b053D9083451bBAB84c538ff2Cc701d)
```
