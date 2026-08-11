---
title: "CMMC Phase 2 Is Suspended. Your Legal Exposure Went Up."
date: 2026-08-11
lastReviewed: 2026-08-11
draft: false
tags: ["CMMC 2.0", "NIST 800-171", "DFARS", "False Claims Act", "Defense", "DIB", "Compliance"]
categories: ["Defense"]
summary: "The certification deadline is gone. The obligations are not, and the one government mechanism that used to catch a bad SPRS score before a lawyer did is paused. Here is what defense contractors should actually be working on."
author: "Cameron Hopkin"
---

On July 13, 2026, the Department of Defense announced the immediate suspension of Phase 2 of the CMMC program. The memo behind the announcement is dated July 10 and signed by Chief Information Officer Kirsten Davies, under the Department of War branding the administration has adopted pending a congressional rename. It suspends the November 10, 2026 requirement for third-party C3PAO certification as a condition of award, and it halts the Phase 3 and Phase 4 milestones behind it. It also stands up a CMMC Reform Task Force with 60 days to review the program and come back with recommendations.

The reason given was cost. [DoD officials said the math did not work](https://defensescoop.com/2026/07/13/dod-halts-cmmc-cybersecurity-requirements-phase-2/) for small and mid-sized businesses, and the Small Business Administration had been reporting that assessment costs were pushing companies out of the defense supply chain entirely. Anyone who quoted a small manufacturer a $75,000 assessment against a $400,000 annual DoD revenue line already knew this. The program was going to shrink the industrial base it was designed to protect.

I wrote a post in March laying out the Phase 2 timeline and telling readers that if they handled CUI and had no plan ending in a C3PAO assessment, they were planning to lose contracts. That specific deadline is gone. I am not going to pretend otherwise, and I am not going to quietly leave the old post up as if nothing happened.

But the conclusion most contractors are drawing from this news is wrong, and it is wrong in a direction that can cost them a great deal more than an assessment would have.

## What actually went away, and what did not

The suspension is narrow. It removes the government's requirement that a third party verify your compliance before you win work. Here is what survived it, all of it still binding today:

**DFARS 252.204-7012** still applies to every contract that involves covered defense information. The safeguarding requirement, the requirement to implement NIST SP 800-171, and the 72-hour cyber incident reporting obligation are untouched. This clause has been in contracts since 2017. It never depended on CMMC.

**All 110 NIST SP 800-171 Rev. 2 controls** remain mandatory. Not recommended. Mandatory, by contract.

**Self-assessment and SPRS scoring** continue. Level 1 and Level 2 self-assessments are still required, and you still post the score.

**DFARS 252.204-7021** still requires you to maintain your CMMC status for the duration of the contract and to complete the annual affirmation.

**Flow-down to subcontractors** is unchanged. If you are a prime, your suppliers still owe you the same thing.

**DFARS 252.240-7997**, which was renumbered from 252.204-7020 effective February 1, 2026, still authorizes the government to audit your NIST 800-171 implementation.

Read that list again and notice what it adds up to. Every substantive obligation is intact. What changed is who checks your work, and the answer is now nobody, at least for the moment. DoD also paused DIBCAC assessments during the review period.

That is not relief. That is the removal of a safety net.

## The term you are looking for is the False Claims Act

When people ask me about the risk of getting caught overstating their compliance, they usually describe it as "lying to the government" and then trail off, because they know there is a specific name for it and cannot remember which one. There are two, and the distinction matters.

The civil one is the [False Claims Act](https://www.law.cornell.edu/uscode/text/31/3729), 31 U.S.C. § 3729. It is the one that actually reaches defense contractors in practice. It imposes liability when you knowingly submit a false claim for payment or a false statement material to a claim. "Knowingly" is doing a lot of work in that sentence, and it is broader than most people assume: it covers actual knowledge, deliberate ignorance, and reckless disregard for the truth. You do not need intent to defraud. Not bothering to check is enough. Damages are trebled, and civil penalties are assessed per false claim, which for a contractor submitting monthly invoices under a multi-year contract compounds fast.

The criminal one is [18 U.S.C. § 1001](https://www.law.cornell.edu/uscode/text/18/1001), the false statements statute. It covers knowingly making a materially false statement in a matter within federal jurisdiction, and it carries up to five years. It is charged far less often in this context, but the senior official affirmation in SPRS is exactly the kind of signed statement it contemplates.

Two more mechanics worth knowing. First, the False Claims Act has a qui tam provision, which means a private party can file suit on the government's behalf and collect between 15 and 30 percent of the recovery. That private party is usually a former employee, and very often it is a former IT administrator or security lead who watched a score get inflated and remembered it. Second, the statute of limitations runs six years from the violation, extendable to as long as ten. The SPRS score you post this month is a legal statement that stays actionable well into the next decade.

The Justice Department has been pursuing these cases through its Civil Cyber-Fraud Initiative since 2021. [MORSECORP paid $4.6 million](https://www.justice.gov/opa/pr/defense-contractor-morsecorp-inc-agrees-pay-46-million-settle-cybersecurity-fraud) and [Raytheon paid $8.4 million](https://www.justice.gov/opa/pr/raytheon-companies-and-nightwing-group-pay-84m-resolve-false-claims-act-allegations-relating) in 2025. Cybersecurity-specific FCA settlements rose 233 percent that fiscal year. Not one of those cases was triggered by a breach. They were triggered by the accuracy of the compliance claim.

## LOGZONE is the case to read

In June 2026, a month before the suspension, DOJ [settled with LOGZONE Inc.](https://fcablog.sidley.com/2026/06/23/doj-reaches-507144-settlement-with-defense-contractor-signals-increased-fca-scrutiny-of-cybersecurity-self-assessments/) of Huntsville, Alabama for $507,144 over cybersecurity requirements in Navy contracts.

The numbers are what make this case worth your attention. In October 2021, LOGZONE self-assessed and posted an SPRS score of 110, which is a perfect score, meaning every one of the 110 requirements fully implemented. In February 2024, DIBCAC ran an independent assessment and scored them at negative 170.

The gap between those two numbers is 280 points. That is not a rounding error or a good-faith disagreement about whether a control is adequately implemented. A score of 110 says you have done everything. A score of negative 170 says most of the high-value controls were absent. Somebody sat down, decided what they wished were true, and typed it into a federal system.

Note the timeline. The false score went in during 2021. The government assessment that exposed it came in 2024. The settlement landed in 2026. Five years between the statement and the consequence, and the consequence arrived anyway.

## Why the suspension raises your exposure instead of lowering it

Here is the part I would want a client to sit with.

Before July, there were two paths by which a wrong SPRS score got corrected. A C3PAO assessment, coming for you eventually under Phase 2, would surface the gap and you would fix it. Or DIBCAC would show up and surface it the hard way. Either way there was a professional, technical, non-litigious mechanism that found the discrepancy and turned it into a remediation project.

Both of those are now paused. The affirmation requirement is not. You are still signing, and now you are the only one looking.

What that means practically is that the discrepancy between your claimed score and your real posture no longer gets discovered by an assessor. It gets discovered later, by a former employee with a lawyer, or by DIBCAC whenever assessments resume and with several more years of affirmations stacked up behind the original misstatement. The correction mechanism was removed. The liability mechanism was not. That is the whole picture in two sentences.

I want to be fair about the counterargument, because there is a real one and you will hear it from people who are not being irresponsible. Some defense counsel have pointed out that suspending the certification requirement arguably undercuts the government's own position that CMMC compliance is material to the payment decision, and materiality is a required element of an FCA claim after the Supreme Court's decision in *Escobar*. That argument is not frivolous.

It is also not a plan. It applies to CMMC certification specifically, not to DFARS 252.204-7012, which the government has enforced independently for years and which was the basis for MORSECORP and LOGZONE alike. It is an argument your lawyer makes after you have been sued, at considerable expense, with an uncertain outcome. Building a compliance posture on the theory that the government has weakened its own materiality case is a strange way to run a defense business.

## What to work on between now and the task force report

The Task Force recommendations are due around September 11, 2026, 60 days from the announcement. Nobody knows what they will say. The plausible outcomes range from a lighter-weight assessment tier for small businesses, to a longer runway with the same endpoint, to something closer to permanent reliance on self-attestation with sharper enforcement teeth. Every one of those outcomes rewards a contractor who used this window to actually close gaps, and punishes one who used it to stop.

Six things, in order:

1. **Re-score yourself honestly, right now, against the environment you actually have.** Use the DoD Assessment Methodology and the real point values. Read the assessment objectives, all 320 of them across the 110 requirements. Do not give yourself credit for a control because you bought a product that could implement it. If your honest score is 47, your score is 47.

2. **If your posted SPRS score is wrong, fix it and document why.** This is the single highest-value thing most contractors reading this can do this month. Correcting a score is not a confession, and a contemporaneous record showing you reassessed, found the delta, corrected it, and built a remediation plan is close to the strongest evidence there is against the "reckless disregard" standard. A score that quietly stays wrong is the thing that becomes a case. Talk to counsel before you make a large correction if the original score supported awards you have already been paid on, because that specific scenario has nuances worth an hour of a lawyer's time.

3. **Treat the annual affirmation as the legal document it is.** Whoever signs it should understand that they are personally attesting to the government. That person should be reviewing the underlying assessment, not initialing a form an administrator put in front of them. If the senior official signing is not comfortable defending the number in a deposition, the number is not ready to submit.

4. **Finish the 5-point and 3-point controls.** Multifactor authentication, FIPS-validated encryption for CUI at rest and in transit, audit logging, and access control are where the scoring weight lives and where the DIBCAC delta almost always comes from. These are also the controls that actually reduce the odds of the breach that starts the whole conversation.

5. **Keep building the enclave.** The scoping logic did not change because the deadline did. Isolating CUI to the smallest defensible footprint is what makes the 110 controls affordable, and it is the difference between a project you can finish and one you abandon. Twenty workstations is a manageable problem. Two hundred is a different company.

6. **Keep your SSP current.** DFARS assumes you maintain one. It is the document that proves what you claimed and when you claimed it, and if you ever do have to answer for a score, the SSP and the evidence behind it are your defense.

Notice that this list is nearly identical to what I would have told you in March. That is the point. The work was never really about the certificate. Phase 2 was a deadline attached to the work, and deadlines are useful, but removing a deadline does not remove a contract clause.

## The honest read

If you were three months from a C3PAO assessment and just got the news, you got a genuine reprieve on a real expense, and you should feel fine about that. Take the assessment budget and put it into the 3-point and 5-point gaps instead. You will be in a better position on the merits and a better position legally.

If you were hoping this would go away and it just did, understand precisely what happened: the requirement that someone else check your homework was suspended. The requirement to do the homework, and to sign your name to a statement about it, was not. For a contractor with an inflated score sitting in SPRS, this news made things quietly worse, because the pause removed the most likely path to finding out before a whistleblower does.

An aspirational SPRS score was a liability in March. With DIBCAC paused and the affirmation still due, it is a larger one in August.

Score yourself against the company you have. Post the real number. Then go fix it on a schedule you can defend.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB supporting defense, federal, and commercial organizations through NIST 800-171, DFARS, FedRAMP, and HIPAA compliance engagements. Questions about SPRS scoring, self-assessment defensibility, or CUI scoping can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*

*Nothing in this post is legal advice. If you believe a score you have already submitted may be inaccurate, talk to qualified government contracts counsel before you act.*
