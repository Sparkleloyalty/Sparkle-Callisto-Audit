# Callisto Smart-contract auditing department.
# Free security audits, for the safety of the entire industry.

Callisto Security department performs free security audits for smart-contracts. Our security auditors are paid from [Callisto Treasury](https://github.com/EthereumCommonwealth/Roadmap/issues/48). Anyone can submit a request for security audit of a smart-contract free of charge.

ETC (Ethereum Classic) and CLO (Callisto) Solidity smart-contracts have the highest priority.

If you are using our audit report or announcing it for the general public, proper attribution required: 

"Smart Contract Security Audit by Callisto Network" 

alternatively you can use our verified badge:

![alt text](https://github.com/sneg55/Auditing/blob/master/callisto-badge.png)

Anyone can submit a request of a security audit for an open-source smart-contract. After the creation of a security audit request, we will contact the developers of the smart contract being audited. Until we receive the response from the developers, the audit request will be assigned a `low priority` status. Low priority status is unassigned when we receive the confirmation from the developers. Confirmed audit requests are processed first.

# Submitting an audit request

You can use Smart Contract Audit Request web form on our site: https://callisto.network/smart-contract-audit/ 

or create request directly:

1. Go to Auditing/issues section and click a [New Issue](https://github.com/EthereumCommonwealth/Auditing/issues/new) button.
2. Fill the form and click a "Submit New Issue" button.
3. Follow the comments in the corresponding "issue" discussion.
4. The result of a security audit will be published at the comments once auditors complete their task.

![alt text](https://github.com/EthereumCommonwealth/Callisto-Media-Kit/blob/master/logo-official-twitter_506x253.png)

## Callisto Security Department workflow.

There are two types of participants in the Security Department:
- auditing manager
- security auditors

### Audit requests order (auditing manager)

For smart-contracts, the following order of audits is determined:
- Contracts that are important for the whole cryptocurrency industry, can have the highest priority.
- Contracts intended for deployment in the ETC/CLO network have the highest priority (with the exception of previous paragraph).
- Contracts of the ETH network have medium priority.
- Other contracts have low priority.
- If the audit of the smart contract is already started, then it continues until it is completed, regardless of the availability of other contracts with higher priority in the queue.

After the audit request has been created, it is viewed by the audit manager. If the request meets the requirements, then the auditing manager assigns it `approved` status. `approved` label means that the audit request is available for auditors for picking.

If there are several requests with different priorities in the queue, then the manager **should** assign the `approved` status only to contracts with the highest priority. The remaining contracts will be checked after the audit of the contracts with the highest priority has been performed. If there are several contracts in the queue with the highest priority, then the audit manager **should** assign the status of `approved` to all these contracts simultaneously. In this case, the contract that auditors will begin to check first will be checked earlier.

### Performing an audit (security auditor)

After an audit request with an `approved` label appears, an auditor can pick it by commenting the issue and indicating how much time it should take to audit this smart-contract (roughly/ in days). After that, the auditor can start reviewing the code immediately. Other community members **may** also pick the request and submit their audit reports. These reports **must** be reviewed by auditor manager at the end of the auditing process. If the audit request was approved, but none of the auditors picked it, then the audit manager can appoint auditors to check this request if they are not engaged in checking another smart-contract.

Auditing manager **must** comment that the audit is successfully started and mention github nicknames of all the auditors which will be responsible for the check of the corresponding contract after several auditors have picked the issue-request. The audit manager **must** also comment his contact email, to which the auditors will send their secret gists (audit reports).

After the auditor began to check the code, he **must** create a **secret** [github gist](https://gist.github.com/) and send it to the auditing manager by email. An auditor **must not** reveal the audit report gist or publish it anywhere, so that only auditing manager and auditor (gist owner) could review it during the auditing process.

After the auditor has completed the verification of the code, he should comment to the appropriate issue that his audit report is completed. NOTE: An auditor **must not** reveal his report gist!

### Completion of the audit

After all the responsible auditors have completed their reports, the audit manager must compare the reports.

If there are no significant discrepancies in the reports and no critical errors are detected, then the audit manager **must** complete the audit by summarizing the reports and submitting secret gist urls in the comment of the corresponding audit request-issue. The audit is considered complete after all the responsible auditors have submitted their reports, and the audit manager has summarized the results of these reports and published report gist urls.

If one of the community members has expressed a desire to participate in the audit of this contract and also sent his report to the audit manager, then the audit manager **must** review the report and comment its secret gist url to the corresponding github request-issue regardless of whether the audit was already completed or not.

### Disclosure policy

After the audit was completed, the audit manager **may** inform the customer about the results without revealing the reports. After 15 days from the date of informing the customer about the findings, the reports should still be published and the results summed up.

## Security Auditor's Salary

After an auditor completes a smart contract audit, he receives a reward which dependents from contract complexity and work quality. When hiring, an auditor can choose the base currency (CLO or USD) of the salary, but he can't change it in the future.

 `An auditor's reward = contract reward * ratio`

|Contract Complexity|Reward, CLO|Reward, USD|
|---|---|---|
|High|80,000|800|
|Medium|40,000|400|
|Mid-Low|20,000|200|
|Low|10,000|100|

| Work quality | Ratio | Description |
|---|---|---|
|Excellent|ratio 1|Found all medium and high severity issues|
|Good|ratio 1/2|Found some medium and/or high severity issues and missed some medium severity issues|
|Satisfactory|ratio 1/4|Found some medium and/or high severity issues and missed some high severity issues|
|Poor|ratio 1/8|Missed all medium and/or high severity issues|
|Average|ratio 1/3|A contract has not any medium and high severity issues|

# Security Auditor's guide

## What the auditor of smart-contracts should do.

The main task of each security auditor is to check the code for security-related mistakes and write a report on the detected errors after the audit is completed.

1. All the work will be coordinated through github. Each auditor **must** visit the [Auditing/issues](https://github.com/EthereumCommonwealth/Auditing/issues) repository section every (working) day.

If an audit request (issue) which is labeled `approved` appears in the list,  the auditor **may** pick it. The audit manager can also appoint an auditor if he is not currently engaged in any smart contract checking, by mentioning their github nicknames in the corresponding issue. If the auditor was appointed to a certain issue by the auditing manager, then the auditor **must** perform a verification of the corresponding contract.

2. After the auditor has received the objective of his work, he **must** comment the time that, in his opinion, will be required to verify this smart-contract. 

3. The auditor **must** create a **secret** gist (audit report template) and send it to the auditing manager by email. WARNING: the auditor must never reveal the gist url. It will be revealed by auditing manager at the end of the auditing process. The secret gist should be named as follows: `NETWORK_contract_name_report.md`

Example: `ETH_the_dao_report.md`

4. The auditor **must** check the contract code, perform necessary testing and describe findings at the secret gist (audit report).

Other auditors, community members and the audit manager will also check this smart contract, so the auditor is not incentivised in hiding the errors found or trying to exploit them.

5. After the auditor has completed the verification of the code and supplemented his report with a description of the findings, he should comment the corresponding issue that his report is finished.

# Audit Report template

The audit report name should start with a capital letter. Use underscores instead of spaces between words, write reports in `.md` format.

The report should contain a title describing to which contract or contract system the report belongs.

The report should contain the following sections:

## 1. Summary

Briefly describe the audit report, the purpose of a contract (or contract system) that was reviewed and key features of the contract.

*This may be important to understand the inner logic of the contract or a contract system.*

## 2. In scope

Specify the range of contracts, the version of the contracts that have been verified. If the source code was published on Github, then specify the commit hash.

#### 2.1 Excluded (optional)

Specify which files or contracts were not checked during the audit if there were any contracts/files that were excluded for some reason.

## 3. Findings

Summarize the total amount of mistakes and their severity.

## 3.x Error ( `severity` )

*Describe each bug/mistake/error separately*

Severity assigning:

- high - vulnerability can be exploited at any time and cause a loss of customers funds or a complete breach of contract operability. *(Example: [Parity Multisig hack](https://medium.com/@Pr0Ger/another-parity-wallet-hack-explained-847ca46a2e1c), a user has exploited a vulnerability and violated the operability of the whole system of smart-contracts (Parity Multisigs). This could performed regardless of external conditions at any time.)*

- medium - vulnerability can be exploited in some specific circumstances and cause a loss of customers funds or a breach of operability of smart-contract (or smart-contract system). *(Example: [ERC20 bug](https://gist.github.com/Dexaran/ddb3e89fe64bf2e06ed15fbd5679bd20), a user can exploit a bug (or "undocumented opportunity") of `transfer` function and occasionally burn his tokens. A user can not violate someone else's funds or cause a complete breach of the whole contract operability. However, this leads to millions of dollars losses for Ethereum ecosystem and token developers.)*

- low - vulnerability can not cause a loss of customers funds or a breach of contracts operability. However it can cause any kind of problems or inconveniences. *(Example: [Permanent owners of multisig contracts](https://gist.github.com/Dexaran/2389d5e7290ab69709d33abfe0485bec#1-permanent-ownership), owners are permanent, thus if it will be necessary to remove a misbehaving "owner" from the owners list then it will require to redeploy the whole contract and transfer funds to a new one.)*

- minor observation - other code flaws, not security-related issues.

#### Code snippet

Give a link to a fragment of code that can lead to an error that you describe.

#### Description

Describe this finding in detail.

#### Recommendation (optional)

Write down how the bug can be fixed if you know how to do it. However, fixing bugs is not the primary goal of the security auditor.

## 4. Conclusion

Describe the most important findings and their relationship to the main purpose of the contract. Describe how the internal logic of the contract is related to its purpose.
Indicate whether the contract is safe or any critical problems needs to be resolved.

# Example: ETC multisig audit report

https://gist.github.com/Dexaran/2389d5e7290ab69709d33abfe0485bec

