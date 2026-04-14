---
title: "CMMC Level 2 for Small Businesses: What Actually Changed"
date: 2026-03-14
draft: false
tags: ["CMMC 2.0", "NIST 800-171", "Defense", "DIB", "Compliance"]
categories: ["Compliance"]
summary: "The final rule is live. Here is what small defense contractors need to know about scoping, POA&M timelines, and what assessors are actually looking for."
author: "Cameron Hopkin"
---

The CMMC program is no longer a future problem. It is a contract clause with a deadline that is already inside the planning horizon for anyone running a small defense business in 2026.

Two final rules now govern the program. [32 CFR Part 170](https://www.ecfr.gov/current/title-32/subtitle-A/chapter-I/subchapter-G/part-170) took effect on December 16, 2024 and defines the policy, the maturity levels, the assessment methodology, and the rules about what you can and cannot put on a Plan of Action and Milestones. The [48 CFR final rule](https://www.federalregister.gov/documents/2025/09/10/2025-17359/defense-federal-acquisition-regulation-supplement-assessing-contractor-implementation-of) published in the Federal Register on September 10, 2025 and became effective November 10, 2025. This is the one that put CMMC language into DFARS and gave contracting officers the authority to require it at award.

Phase 1 started on that November 10, 2025 effective date. Self-assessments are live in contracts today, and the DoD already has discretion to require C3PAO certification for priority work. Phase 2 starts November 10, 2026, and that is the date that matters for most readers of this post. On that date, third-party Level 2 certification by a C3PAO becomes a condition of award for any contract involving Controlled Unclassified Information. Phase 3 follows in November 2027. Phase 4, full implementation across every applicable contract, begins November 10, 2028.

If you handle CUI and you do not have a plan that ends in a C3PAO assessment before Phase 2, you are planning to lose contracts.

## The scoring math most small businesses get wrong

CMMC Level 2 is scored against the 110 security requirements in NIST SP 800-171 Revision 2. Each requirement is weighted 1, 3, or 5 points based on how critical it is to protecting CUI. A perfect implementation scores 110. A poorly implemented environment can score negative. The practical floor on SPRS is roughly minus 203. That is not a typo.

To qualify for Conditional Level 2 status you need a minimum score of 88 out of 110, which is 80 percent. That gets you on the field. It does not finish the game.

Here is the part that trips up nearly every first-time contractor I have talked to: POA&Ms are not a list of things you will fix someday. Under 32 CFR 170.21, a POA&M item must be a 1-point requirement, with one narrow exception for SC.L2-3.13.11 (CUI encryption) when encryption is present but not FIPS-validated. Every 3-point and 5-point requirement has to be MET at the time of assessment. There is no partial credit at the top of the pyramid.

Six specific 1-point items are also explicitly excluded from POA&M use. The rule is clear that your System Security Plan, any requirement tied to core CUI protections, and a handful of others must be fully implemented on day one. Show up with those on a POA&M and your assessment will not pass.

Once you earn Conditional status, you have 180 days from the Conditional CMMC Status Date to remediate every item on your POA&M and complete a closeout assessment. Miss the window and your Conditional status expires. Expiration during a contract period of performance triggers standard contractual remedies, which is the polite phrase for "you lose eligibility for any contract with a Level 2 requirement on that information system."

## Scoping is the decision that determines everything else

The single most expensive mistake I see in small-business CMMC work is over-scoping. Contractors decide that "CMMC applies to us" and proceed to drag every laptop, every cloud app, every shared drive, every personal device, and every contractor into assessment scope. Then they try to harden it all. Then they run out of budget. Then they either quit or fail.

The opposite mistake is nearly as expensive. Under-scoping, where you claim a boundary that does not match how CUI actually moves through your environment, is an automatic assessment failure. An assessor who finds CUI on a workstation that is not listed in your asset inventory is not going to negotiate.

The CMMC Assessment Scope is defined in [32 CFR 170.19](https://www.ecfr.gov/current/title-32/subtitle-A/chapter-I/subchapter-G/part-170/subpart-D/section-170.19). Every asset in your environment falls into one of five categories:

1. **CUI Assets** — systems that process, store, or transmit CUI or Security Protection Data. These must meet all 110 requirements.
2. **Security Protection Assets (SPAs)** — things like firewalls, identity providers, MFA services, SIEMs. They provide security functions to the CUI environment and are assessed against the controls relevant to that function. A common trap here: most small businesses with an MSP assume the MSP is out of scope because it is external. It is not. If the MSP manages your firewalls or identity, it is an SPA and its services are in scope.
3. **Contractor Risk Managed Assets (CRMAs)** — assets that could access CUI but are not designed to. They are in scope but assessed against a reduced set of controls, with a heavier reliance on policy and user discipline. Assessors can and do test these.
4. **Specialized Assets** — OT, IoT, test equipment, government furnished equipment, restricted information systems. These get a limited assessment against NIST 800-171 controls that can reasonably apply, with the rest documented in the SSP.
5. **Out-of-Scope Assets** — physically or logically separated from the CUI environment, with no ability to reach CUI or security protection data. These must still be documented as out-of-scope in the SSP. The assessor can challenge the claim.

You are the one proposing the boundary. The C3PAO can accept it, challenge it, or reject pieces of it. The best thing you can do for your assessment is to design a tight, defensible enclave that isolates CUI to the smallest practical footprint, and to back that boundary with network diagrams, data flow maps, and an asset inventory that matches reality down to the device.

For most small defense contractors, the right architecture is a CUI enclave: a logically separated environment used only by people who need CUI to do their jobs, with its own identity, its own endpoints, its own collaboration tools, and a hard boundary to the rest of the business. Securing 20 workstations is not the same kind of project as securing 200.

## FCA enforcement is the new tail risk

CMMC changed the legal exposure around cybersecurity compliance in a way a lot of small businesses have not thought through yet.

The 48 CFR rule requires an annual senior official affirmation in SPRS. That affirmation is a certification to the government that your score and your implementation status are accurate. The same rule requires contractors to update their SPRS score whenever their environment materially changes. Contracting officers are required to check SPRS before award and before exercising options.

Those two mechanisms together create a measurable, time-stamped, legally significant statement of compliance. When a C3PAO assessment later produces a result that does not line up with the SPRS score a contractor claimed, the gap between the two is no longer a compliance gray area. It is a potential False Claims Act case.

The Department of Justice has already been active here. [MORSECORP paid $4.6 million in 2025](https://www.justice.gov/opa/pr/defense-contractor-morsecorp-inc-agrees-pay-46-million-settle-cybersecurity-fraud) to resolve allegations that it falsely represented its compliance with DFARS 252.204-7012 cybersecurity requirements. [Raytheon agreed to pay $8.4 million](https://www.justice.gov/opa/pr/raytheon-companies-and-nightwing-group-pay-84m-resolve-false-claims-act-allegations-relating) in related settlements. Neither case was triggered by a breach. Both were triggered by the accuracy of the compliance claim itself.

The honest takeaway for a small contractor is this: an aspirational SPRS score is now a liability, not a shortcut. Score yourself against the environment you actually have, not the environment you are planning to have next quarter. If your real score is 62, put 62 in SPRS. If your real score is negative, put it in negative. Then get to work closing the gap on a defensible schedule.

## What to do this week

Six things, in order:

1. **Confirm whether you touch CUI at all.** If your contracts only involve Federal Contract Information, you are a Level 1 contractor and your path is dramatically simpler: the 15 practices in FAR 52.204-21, an annual self-assessment, an annual affirmation. No POA&Ms at Level 1. If your contracts reference DFARS 252.204-7012 or specifically call out CUI handling, you are a Level 2 contractor and the rest of this list applies.

2. **Scope your CUI environment honestly.** Find where CUI actually lives. Email, file shares, engineering workstations, any MSP who touches security functions, any cloud service that holds or transmits it. Map it on paper first. Then decide whether an enclave architecture makes sense for the size of the footprint you just drew.

3. **Self-assess against NIST 800-171 Rev 2 using the DoD Assessment Methodology.** Use the actual scoring values. Do not round up. Do not assume "we have antivirus" means you meet SI.L2-3.14.2. Read the assessment objectives. There are 320 of them across the 110 requirements. Each one has to be met or not met.

4. **Post your honest score to SPRS and have a senior officer affirm it.** This is a legal statement. Make sure it is one you can defend.

5. **Build your POA&M with the real rules in mind.** Every 3-point and 5-point gap has to be closed before assessment. Only 1-point items belong on the POA&M, and only some of those. If you are sitting on a 3-point gap at multi-factor authentication or FIPS-validated encryption, you do not have a POA&M item. You have a remediation project that has to finish before you schedule an assessment.

6. **Book a C3PAO 9 to 12 months ahead of your target date.** There are [roughly 100 authorized C3PAOs](https://cyberab.org/Catalog/Certified-Assessors-and-Instructors/Certified-Third-Party-Assessor-Organizations) serving approximately 76,000 organizations that will need Level 2 certification. The bottleneck is real. Small-to-mid-sized assessment engagements are currently trending near $75,000, though scope and complexity drive that number significantly in both directions.

None of this is optional if you plan to keep doing DoD business after November 10, 2026. The rule has already happened. The contracts have already started landing. The question in front of every small defense contractor right now is not whether to engage with CMMC. It is how fast and how cleanly you can move.

The good news is that a small business with a tight scope, a clean enclave, and an honest assessment can earn Level 2 certification faster and at a lower cost than most of the industry is telling you. Complexity is something you add. Starting simple and staying simple is its own compliance strategy.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB supporting defense, federal, and commercial organizations through CMMC, NIST 800-171, FedRAMP, and HIPAA compliance engagements. Questions about CMMC scope, POA&M strategy, or assessment readiness can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*
