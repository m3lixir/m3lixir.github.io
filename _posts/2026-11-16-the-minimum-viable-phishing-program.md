---
layout: post
title: "The Minimum Viable Phishing Program"
date: 2026-11-16 19:59:54-0500
description: "A practical phishing resilience program for the administrator doing everything else, too."
tags: [phishing, security-awareness, small-business, cybersecurity]
categories: [security]
published: true
related_posts: false
pretty_table: true
toc:
  sidebar: left
---

**By Melisa K. Savich**

A phishing program doesn’t need a dedicated security team or an elaborate dashboard. It needs a reliable reporting path, someone prepared to respond, and a way to learn whether both work.

For a business with 5–50 employees, the minimum viable program has four parts: realistic scenarios, an easy way to report suspicious messages, short exercises, and useful measurements. Start with what you already have. Add tooling when it solves a specific problem.

This program has two companion repositories:

- [Minimum Viable Phishing Training](https://github.com/m3lixir/minimum-viable-phishing-training) provides a short employee guide, discussion exercises, and facilitator materials.
- [Minimum Viable Phishing Campaign](https://github.com/m3lixir/minimum-viable-phishing-campaign) demonstrates campaign planning and reporting metrics with synthetic data.

The campaign project runs locally. It does not send emails, collect credentials, or conduct live phishing simulations.

## Start with the business, not the bait

Threat modeling can fit on one page. Ask: **What could an attacker persuade someone here to do, and what would happen next?**

| Priority | Scenario | Likely target | Desired response |
|---|---|---|---|
| 1 | Vendor requests a payment change | Whoever pays invoices | Verify through an independently sourced phone number |
| 2 | Fake account alert asks for a sign-in | Anyone with a business account | Open the service directly and report the message |
| 3 | Unexpected shared document | Staff working with outside organizations | Verify the sender and expected document |

Adjust the order to match your workflows. Ask employees what legitimate requests look like; their answers reveal where impersonation would be most convincing.

Awareness is one control, not the entire defense. Enable phishing-resistant multifactor authentication where practical, restrict administrative access, and independently verify payment changes.[^cisa-fbi]

## Choose the smallest toolset

| Option | What it provides | Tradeoff |
|---|---|---|
| **Microsoft 365** | Outlook reporting and configurable submission routing; Attack simulation training provides managed campaigns and reports | Attack simulation training requires Microsoft 365 E5 or Defender for Office 365 Plan 2. |
| **Google Workspace** | Gmail’s built-in **Report phishing** action and administrative email-security features | Reporting to Google is not a simulation campaign. Establish and test a separate path to your administrator. |
| **GoPhish** | Open-source, self-hosted campaign management, event exports, and reporting integration | You maintain and secure the infrastructure; reporting integration requires configuration. |
| **Tabletop exercise** | A sample message discussed in a meeting | Low overhead, but it does not measure behavior in an actual inbox. |

Microsoft can route supported user reports to a reporting mailbox, Microsoft, or both. Test the configuration in the Outlook clients your staff actually use.[^microsoft-routing][^microsoft-simulations] Gmail users can select **More → Report phishing**, but don’t assume that action also creates an internal IT ticket.[^google]

GoPhish supports reporting through a configured mailbox, but it adds operational overhead.[^gophish] If a tabletop meets your current needs, start there.

## Build the reporting loop first

Give employees one primary instruction and one fallback:

> ##### Reporting a suspicious message
>
> Use the configured report button. If it isn’t available, forward the message as an attachment to the designated security mailbox.
>
> If you entered a password, approved an unexpected sign-in, or sent money, contact IT immediately through the urgent channel.
{: .block-tip }

Replace those placeholders with real, monitored destinations. Test the process on desktop and mobile. Make clear that reporting after clicking is still useful.

For the administrator, document a short response procedure:

1. Acknowledge the report and record when it arrived.
2. Inspect the sender, headers, links, and context without interacting with suspicious content.
3. Determine whether others received the message and use available mail-platform remediation tools.
4. Follow the incident procedure if an account or payment may be compromised.
5. Close the loop with the reporter and record the outcome.

Set a target that matches your coverage—for example, acknowledging reports within one business hour when IT is staffed. Define an escalation contact for urgent incidents outside that window.

## Train employees to respond

Start with a 15-minute session on three actions: **pause, verify, and report**. Demonstrate the reporting process and explain what to do after clicking a link, entering information, or approving an unexpected sign-in.

Use examples that match employees’ work. Someone responsible for invoices should practice verifying payment changes; everyone should know how to check an unexpected account alert or shared document.

The [training repository](https://github.com/m3lixir/minimum-viable-phishing-training) includes a facilitator guide and three discussion scenarios. Revisit the material during onboarding and after an exercise. Record participation, but don’t treat completion as proof that someone can recognize every phish.

## Run a safe exercise

Get written authorization covering participants, dates, scenarios, retention, and who can see results. Tell employees that exercises occur and explain their purpose. Coordinate with whoever manages mail security, then test the reporting path before starting.

Begin with one scenario and a small pilot. Use a benign landing page that explains the exercise. Do not collect passwords, MFA codes, or other sensitive information. Avoid themes involving layoffs, medical emergencies, or unnecessary personal distress.

If delivery requires an exception, document its scope and expiration. A message deliberately allowed through tests employee response under that condition; it does not demonstrate that normal mail protections failed.

Afterward, explain what the message asked the recipient to do, how to verify that request, and how to report similar messages.

## Measure more than clicks

Record the scenario, audience, observation window, confirmed deliveries, and difficulty. A simple **easy / moderate / hard** label is useful context, but it is not a formal NIST Phish Scale assessment.[^nist]

Track these measures together:

- **Reporting rate:** Unique recipients who reported ÷ confirmed delivered messages.
- **Time to first report:** The first report timestamp minus that recipient’s delivery timestamp.
- **Median acknowledgment time:** Median time between a report and IT acknowledgment; include the number acknowledged and the observation window.
- **Delivery failures and exclusions:** Track separately from employee behavior.
- **Scenario context:** Note difficulty, warning banners, timing, and any delivery exceptions.

A person can click and then report. Automated security tools can also generate interaction events. With a small audience, one person can substantially change a percentage, so show counts alongside rates and avoid individual leaderboards.

The [campaign PoC](https://github.com/m3lixir/minimum-viable-phishing-campaign) calculates reporting rate, time to first report, and median acknowledgment time from synthetic events. Its output illustrates the calculations; it is not a readiness benchmark.

To try it locally:

```bash
python3 report.py sample_data.json results.md
```

## Roll it out in 90 days

| When | Action | Deliverable |
|---|---|---|
| **Days 1–30** | Identify three scenarios, configure reporting, test the response path, and assign ownership. | Threat list and working reporting procedure |
| **Days 31–60** | Explain the program, deliver training, run a tabletop or authorized pilot, and provide feedback. | Exercise record and lessons learned |
| **Days 61–90** | Review counts and response times, fix a process gap, and decide whether to repeat or expand. | Revised procedure and next exercise date |

Afterward, review the reporting queue regularly, test the reporting path monthly, and revisit scenarios and response procedures quarterly.

### Implementation checklist

- [ ] Assign an owner, backup, and urgent escalation path.
- [ ] Document three realistic scenarios and their desired responses.
- [ ] Test reporting and acknowledgment end to end.
- [ ] Train employees on verification, reporting, and what to do after a mistake.
- [ ] Obtain written authorization before a live simulation.
- [ ] Use benign content and avoid collecting sensitive information.
- [ ] Record deliveries, reports, timing, difficulty, and exceptions.
- [ ] Share feedback and fix at least one identified gap.
- [ ] Restrict access to results and define a retention period.

The goal is a program that makes suspicious messages easier to surface and faster to handle, while reducing the consequences when one gets through.

## References

[^cisa-fbi]: Cybersecurity and Infrastructure Security Agency, & Federal Bureau of Investigation. (2024). *How to protect against Iranian targeting of accounts*. https://www.cisa.gov/sites/default/files/2024-10/cisa-fbi-protecting-against-irgc-phishing-508c.pdf

[^microsoft-routing]: Microsoft. (n.d.). *Configure user reported message settings in Microsoft Defender for Office 365*. Microsoft Learn. https://learn.microsoft.com/microsoft-365/security/office-365-security/user-submission

[^microsoft-simulations]: Microsoft. (n.d.). *Get started using Attack simulation training*. Microsoft Learn. https://learn.microsoft.com/microsoft-365/security/office-365-security/attack-simulation-training-get-started

[^google]: Google. (n.d.). *Avoid and report phishing emails*. Gmail Help. https://support.google.com/mail/answer/8253

[^gophish]: GoPhish. (n.d.). *Email reporting*. GoPhish user guide. https://docs.getgophish.com/user-guide/documentation/email-reporting

[^nist]: Dawkins, S., & Jacobs, J. (2023). *NIST Phish Scale user guide* (NIST Technical Note 2276). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.TN.2276