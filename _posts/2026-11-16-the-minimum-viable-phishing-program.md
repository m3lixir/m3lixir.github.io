---
layout: post
title: "The Minimum Viable Phishing Program"
date: 2026-11-16 19:59:54-0500
description: "Five practical steps to build a phishing program for a small team."
tags: [phishing, security-awareness, small-business, cybersecurity]
categories: [security]
published: true
related_posts: false
toc:
  sidebar: left
---

*A practical guide for the administrator doing everything else, too.*

<figure class="phishing-hero">
  <img
    class="phishing-hero-light"
    src="{{ '/assets/img/blog/minimum-viable-phishing-program/hero-light.png' | relative_url }}"
    alt="A cursor approaching a button suspended from a fishing hook."
  >
  <img
    class="phishing-hero-dark"
    src="{{ '/assets/img/blog/minimum-viable-phishing-program/hero-dark.png' | relative_url }}"
    alt="A cursor approaching a button suspended from a fishing hook."
  >
</figure>

<style>
  .phishing-hero img {
    width: 100%;
    height: auto;
    border-radius: 8px;
  }

  .phishing-hero .phishing-hero-dark {
    display: none;
  }

  html[data-theme="dark"] .phishing-hero .phishing-hero-light {
    display: none;
  }

  html[data-theme="dark"] .phishing-hero .phishing-hero-dark {
    display: block;
  }
</style>

You don’t need a dedicated security team to start a phishing program. You need a reliable reporting path, a way to practice it, and a few useful measurements.

I built two free companion projects to make that easier. Here’s how to get started as a solo administrator supporting 5–50 employees.

## 1. Set up reporting

Choose a primary reporting method and a fallback. Test both in the mail clients employees use:

- **Primary:** A report button configured to reach IT.
- **Fallback:** A monitored security mailbox for suspicious messages forwarded as attachments.

Microsoft can route supported user reports to a reporting mailbox, Microsoft, or both.[^microsoft-routing] Gmail’s **Report phishing** action reports to Google; establish and test a separate path to your administrator.[^google]

> ##### Tell employees
>
> If you clicked a link, entered information, approved an unexpected sign-in, or sent money, contact IT immediately.
{: .block-tip }

## 2. Pick a realistic scenario

Choose one request that fits your workflows: an urgent account alert, a vendor payment change, or an unexpected shared document.

Write down the desired response. For a payment change: **Call the vendor using an independently verified number before changing anything.**

Pair training with technical controls. Phishing-resistant MFA and independent payment verification help reduce the consequences when a message gets through.[^cisa-fbi]

## 3. Train and practice

Spend 15 minutes demonstrating how to **pause, verify, and report**. Then walk through your scenario as a tabletop exercise.

The [training kit](https://github.com/m3lixir/minimum-viable-phishing-training) provides an employee guide, discussion exercises, and facilitator notes. Use it during onboarding and revisit it after exercises.

## 4. Run an authorized simulation

If you choose an email simulation, obtain written authorization and define participants, dates, and who can access results. Use a benign landing page; don’t collect passwords or MFA codes.

Microsoft’s Attack simulation training requires Microsoft 365 E5 or Defender for Office 365 Plan 2.[^microsoft-simulations] GoPhish is open source, but you’ll maintain the infrastructure.[^gophish]

Document any delivery exception. A message deliberately allowed through doesn’t test your normal filtering.

## 5. Measure and adjust

Record confirmed deliveries and unique reporters; divide reporters by deliveries for the **reporting rate**. Also track time to the first report, IT acknowledgment time, and failed deliveries.

Note scenario difficulty: an informal easy/moderate/hard label isn’t a formal NIST Phish Scale score.[^nist] Show counts alongside percentages; one person makes a big difference on a small team.

The [campaign PoC](https://github.com/m3lixir/minimum-viable-phishing-campaign) demonstrates these metrics using synthetic data. It doesn’t send email or run live simulations.

## Your first 90 days

- **Days 1–30:** Set up reporting, assign an owner, and choose a scenario.
- **Days 31–60:** Train employees and run a tabletop or authorized pilot.
- **Days 61–90:** Review results, fix one gap, and schedule the next review.

Afterward, test the reporting path monthly and revisit the procedure quarterly.

Thanks for reading. Start with the [training kit](https://github.com/m3lixir/minimum-viable-phishing-training), then explore the [campaign PoC](https://github.com/m3lixir/minimum-viable-phishing-campaign) when you’re ready to measure results.

## References

[^microsoft-routing]: Microsoft. (n.d.). *Configure user reported message settings in Microsoft Defender for Office 365*. Microsoft Learn. https://learn.microsoft.com/microsoft-365/security/office-365-security/user-submission

[^google]: Google. (n.d.). *Avoid and report phishing emails*. Gmail Help. https://support.google.com/mail/answer/8253

[^cisa-fbi]: Cybersecurity and Infrastructure Security Agency, & Federal Bureau of Investigation. (2024). *How to protect against Iranian targeting of accounts*. https://www.cisa.gov/sites/default/files/2024-10/cisa-fbi-protecting-against-irgc-phishing-508c.pdf

[^microsoft-simulations]: Microsoft. (n.d.). *Get started using Attack simulation training*. Microsoft Learn. https://learn.microsoft.com/microsoft-365/security/office-365-security/attack-simulation-training-get-started

[^gophish]: GoPhish. (n.d.). *Email reporting*. GoPhish user guide. https://docs.getgophish.com/user-guide/documentation/email-reporting

[^nist]: Dawkins, S., & Jacobs, J. (2023). *NIST Phish Scale user guide* (NIST Technical Note 2276). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.TN.2276