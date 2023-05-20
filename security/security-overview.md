# 🛡 Security Overview

Security is a core pillar of our organization, and this section provides a high-level overview of the various security measures we have in place to safeguard our operations.

* [Audits](security-overview.md#audits)
* [Bug Bounty Program (BBP)](security-overview.md#bug-bounty-program)
* [Access / Admin Controls](security-overview.md#access-control)
* [Quality Review - DeFi Safety](security-overview.md#quality-review-defi-safety)
* [Other Achievements](security-overview.md#other-achievements)

### 🛡 Audits

We uphold the highest industry standards by regularly undergoing audits conducted by reputable third-party organizations. Our stETHvv 2.0 and 1.0 contracts, including their dependencies, have been thoroughly audited by organizations such as **OpenZeppelin and ABDK. CredShields** also audited the stETHvv 1.0 version. The full list of audits conducted, along with their reports, can be found on our [GitHub page](https://github.com/pods-finance/yield-contracts/tree/main/audits).

### 🐛 Bug Bounty Program

Our commitment to security also extends to encouraging external contributions through a [Bug Bounty Program](https://immunefi.com/bounty/pods/), hosted on ImmuneFi. By offering rewards of up to **$100,000 or 5% of the funds at risk**, we actively incentivize the discovery and reporting of potential vulnerabilities in our system.

### 🔐 Access Control

In our system, we adopt a layered access control approach. Our smart contracts architecture has been designed to mitigate risks associated with administrative access, permanent freezing of funds, and malicious upgrades. Users can exit their positions at any point, and the withdrawal fee is capped at 10% to avoid unfair fee increases.

A variety of roles are involved in managing our system, each with specific responsibilities:

1. **VaultController**: A 2/3 multisig role responsible for initiating and ending the round in the vault.
2. **ConfigurationManager Owner**: Also a 2/3 multisig role, this role is in charge of setting the VaultController, withdrawal fee ratio, migration contract, and cap of a specific vault.
3. **Investor**: The Investor role, another 2/3 multisig role, is entrusted with utilizing 50% of the weekly yield to buy options at the most advantageous prices.

Each of these roles is designed with stringent access controls to ensure security and transparency within our organization. For a more in-depth explanation of these roles and their permissions, please refer to the specific sections.

### 🏅 Quality Review - DeFi Safety

We are committed to maintaining the highest level of quality and security in our operations. To this end, we recently engaged DeFi Safety, a well-regarded entity in the blockchain space, to conduct an extensive quality review of our system.

We're proud to announce that we scored a remarkable **97%** on their evaluation, placing us in the t**op 5 DeFi projects reviewed by DeFi Safety**. This outstanding result is a testament to the robustness of our security protocols and the diligence of our team.

For full transparency, we have made the complete report available. You can access and review here: [https://defisafety.com/app/pqrs/539](https://defisafety.com/app/pqrs/539)

Our high score reflects our continuous commitment to security and the excellence of our project. It affirms that we're taking the right steps towards building a trustworthy, secure, and reliable DeFi project for our users.

### 🎗 Other Achievements

Our dedication to ensuring top-notch security extends beyond audits and quality reviews. In this section, we'll shed light on some of our other achievements and initiatives that underscore our commitment to security.

#### Event Presentations

We believe in sharing our knowledge and expertise to foster a more secure crypto landscape. Our team had the opportunity to deliver a presentation on security best practices at a renowned crypto event, emphasizing the importance of rigorous security protocols in the development and management of DeFi projects. This presentation allowed us to share our insights and learnings, furthering our role as thought leaders in the space.

* EthCC\[4] - from a Hackathon to your first code audit\
  [https://www.youtube.com/live/\_9LSO09TdvY?feature=share](https://www.youtube.com/live/\_9LSO09TdvY?feature=share)
* Security walkthrough\
  [https://blog.pods.finance/security-status-report-2d617f184502](https://blog.pods.finance/security-status-report-2d617f184502)

#### Recognition on Social Media

Our security efforts have been recognized and applauded by various security companies on social media. These acknowledgments attest to the effectiveness of our security measures and our proactive approach in maintaining a secure environment for our users.

* The first project to implement Trail of Bits Crytic properties:\
  [https://twitter.com/thebensams/status/1635704105523109888](https://twitter.com/thebensams/status/1635704105523109888)
* Fastest payment in a bug bounty from Immunefi:\
  [https://medium.com/immunefi/pods-finance-bug-fix-postmortem-61a576897ebd](https://medium.com/immunefi/pods-finance-bug-fix-postmortem-61a576897ebd)

#### Parallel Projects

In our pursuit of a more secure crypto ecosystem, we've initiated parallel projects focused on security. These projects, while separate from our main operations, aim to explore new methodologies and technologies to enhance security in DeFi projects. One of our examples is a tool to perform long fuzzy testing using Echidna on remote machines:&#x20;

* [https://github.com/pods-finance/remote-echidna](https://github.com/pods-finance/remote-echidna)











