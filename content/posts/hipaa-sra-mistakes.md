---
title: "Five HIPAA SRA Mistakes That Get Practices Fined"
date: 2026-04-14
draft: false
tags: ["HIPAA", "Risk Assessment", "Healthcare", "Compliance", "OCR"]
categories: ["Compliance", "Healthcare"]
summary: "Most security risk assessments fail on the same handful of gaps. We walk through the findings HHS OCR flags most often and how to close them before an audit."
author: "Cameron Hopkin"
---

In October 2024, the HHS Office for Civil Rights launched what it calls the [Risk Analysis Initiative](https://www.hhs.gov/about/news/2024/10/31/hhs-office-for-civil-rights-settles-hipaa-ransomware-cybersecurity-investigation-for-90000-dollars.html). The premise is simple: focus a meaningful slice of OCR's enforcement bandwidth on the single most common Security Rule failure across the regulated entity universe, which is the failure to conduct a real risk analysis.

By the spring of 2025 the initiative had produced eight enforcement actions and roughly $900,000 in settlements. By early 2026 it had reached twelve actions. The settlements span the entire range of regulated entities, from a single-physician imaging practice that paid $5,000 to a national medical supply company that paid $3 million. The common thread in every one of them is the same finding repeated almost verbatim: the organization "failed to conduct an accurate and thorough risk analysis to determine the potential risks and vulnerabilities to the confidentiality, integrity, and availability of all its electronic PHI" as required by [45 CFR § 164.308(a)(1)(ii)(A)](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164/subpart-C/section-164.308).

That sentence appears so often in OCR resolution agreements that you can read a 2025 settlement and predict the language before you scroll to the findings section. It is not a coincidence. It is the most common HIPAA compliance failure in the country, and it is the thing OCR has decided to make expensive.

The good news is that the mistakes are predictable. Five of them account for the vast majority of risk-analysis-related enforcement actions. If your practice or your business associate is doing any of the following, you are sitting on the same risk that produced the 2025 enforcement docket.

## Mistake 1: Calling a compliance gap assessment a risk analysis

These are not the same document.

A compliance gap assessment compares your practice's current state against a checklist of HIPAA requirements and tells you where you are not meeting the standard. It is useful, but it is not what 45 CFR § 164.308(a)(1)(ii)(A) requires. The Security Rule asks for an analysis of the potential risks and vulnerabilities to your specific ePHI, which is a different exercise. It looks at where your data lives, what could threaten it, how likely those threats are, and what the impact would be if they materialized.

The HHS Senior Advisor for Cybersecurity called this out explicitly in a [2023 webinar on the risk analysis requirement](https://www.hhs.gov/hipaa/for-professionals/security/guidance/cybersecurity/index.html), noting that organizations frequently submit gap assessments to OCR investigators and assume they have satisfied the requirement. They have not.

You can tell the difference by what the document produces. A compliance gap assessment produces a list of HIPAA requirements with a yes/no/partial column. A risk analysis produces a list of identified risks with a likelihood rating, an impact rating, an existing-controls description, and a residual risk score. The first is a checklist. The second is a model of how an attacker or a flood or an insider would actually compromise your environment.

[Vision Upright MRI](https://www.hhs.gov/press-room/hhs-hipaa-investigate-vum.html) paid $5,000 and accepted a two-year corrective action plan in May 2025 because their investigator could not find a risk analysis at all. [Comstar](https://www.hhs.gov/press-room/hhs-hipaa-comstar-agreement.html), a billing services business associate that served more than seventy covered entities, paid $75,000 and accepted a similar CAP after a ransomware incident exposed the ePHI of approximately 585,621 individuals. OCR's finding in both cases was the same: no accurate and thorough risk analysis.

The fix is to commission an actual risk analysis aligned with [NIST SP 800-66 Revision 2](https://csrc.nist.gov/pubs/sp/800/66/r2/final), which is the HHS-recognized methodology. If your last "risk assessment" was a vendor giving you a 30-page PDF that listed HIPAA requirements with checkmarks and called it done, you have a gap assessment, not a risk analysis, and OCR will tell you so.

## Mistake 2: An incomplete ePHI inventory

You cannot perform an accurate and thorough risk analysis on data you have not located.

The HHS guidance on risk analysis is clear that the scope of the analysis must include all ePHI that the organization "creates, receives, maintains, or transmits," in any electronic medium, anywhere in the organization's environment. That includes the obvious places, like the EHR and the practice management system, and a long list of less-obvious places that get missed:

- Email accounts where appointment notifications and patient communications flow.
- Voicemail systems that store messages from patients with clinical content.
- Workstations where staff have downloaded files locally for offline work.
- Personal devices enrolled in BYOD programs (and personal devices that are not enrolled but are being used anyway).
- Cloud storage that an office manager set up to share files with a referring practice.
- Backup systems and the offsite copies they generate.
- Imaging systems like PACS, ultrasound machines that store studies locally, and dental imaging consoles.
- Patient kiosks and check-in tablets.
- Fax servers and the spool files they create.
- Vendor systems that hold ePHI under a Business Associate Agreement.
- Old hard drives in storage closets that nobody has wiped.

OCR investigators have called the failure to inventory all systems that store or transmit ePHI one of the most common deficiencies they encounter. The investigator is not going to take your word for it that you know where your data lives. They are going to ask for the asset inventory, and they are going to compare it to the breach report.

The fix is to maintain a living asset and data flow inventory that maps every system handling ePHI, who has access to it, what BAA covers it, and what protections sit around it. The inventory should be updated whenever the practice deploys a new system, signs a new vendor, or onboards a new clinician. It should not be a 2019 spreadsheet that nobody has touched since the last consultant left.

## Mistake 3: Generic templates that ignore your actual environment

Every regulated entity has the same temptation: download a free SRA template, fill in the blanks, save the PDF, file it. The HHS [Security Risk Assessment Tool](https://www.healthit.gov/topic/privacy-security-and-hipaa/security-risk-assessment-tool) is even free and widely used. The problem is not the tools themselves. The problem is treating the tool's questions as the analysis instead of as a starting point for the analysis.

OCR has been explicit that risk analyses must "pertain to the specific operations of the organization." A generic template that does not account for the unique aspects of your network, your workflows, your vendor relationships, and your physical environment is going to miss the risks that actually matter. An imaging practice running a PACS server has different risks than a behavioral health group running a telehealth platform, which has different risks than an EMS billing service running a hosted billing platform with API access into payers. The template cannot tell you any of that.

The HHS Senior Advisor's webinar specifically named "use of template forms or generic tools" as a recurring deficiency. That language matters because it tells you what an investigator is looking for. They want to see that the analysis was tailored, that the practice walked through their actual environment, and that the findings reflect things only an insider would know.

The fix is to use templates as scaffolding and then build the actual analysis on top. Walk the office. Interview the clinicians. Look at the actual configurations on the workstations. Pull the BAA list and trace where the data goes after it leaves your network. Document the conversations. The artifact you produce should be unmistakably yours, not something an investigator could find verbatim on three other practices' SharePoint sites.

## Mistake 4: A risk analysis with no risk management plan

This is the second-most-common failure, and the rule is unambiguous about it. [45 CFR § 164.308(a)(1)(ii)(B)](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164/subpart-C/section-164.308) requires regulated entities to "implement security measures sufficient to reduce risks and vulnerabilities to a reasonable and appropriate level." That implementation specification is paired with the risk analysis specification on purpose. The analysis identifies the risks. The risk management plan addresses them. You need both.

Every 2025 OCR resolution agreement I have looked at requires the entity to do both as part of its corrective action plan. Not because OCR forgot what was in the rule, but because the entities had typically done neither and OCR wants the record to show that the missing pieces are being put in place.

[Northeast Radiology](https://www.hhs.gov/press-room/hhs-ocr-hipaa-settlement-nerad.html) paid $350,000 in April 2025 after OCR found, among other things, that the practice had not conducted a thorough risk analysis. [Deer Oaks](https://www.hhs.gov/press-room/ocr-hipaa-racap-deer-oaks.html), a behavioral health provider, paid $225,000 in July 2025 with a similar finding. Both corrective action plans require the entity to "develop and implement a risk management plan to address and mitigate security risks and vulnerabilities identified in the risk analysis." The phrasing is nearly identical across the resolution agreements because OCR is using a template at this point. The failure is that common.

The fix is to treat the risk analysis as the input to a workplan, not the end of the project. For every identified risk, the practice should document the chosen treatment (mitigate, accept, transfer, avoid), the specific controls being implemented, the owner, the budget, the deadline, and the evidence of completion. That set of artifacts is your risk management plan. When OCR shows up after a breach, the risk analysis answers "did you understand the risk" and the risk management plan answers "what did you do about it." You need clean answers to both.

## Mistake 5: An SRA that is never updated

The 2016-2017 OCR audit, which is still the most comprehensive picture we have of risk analysis compliance across the regulated entity population, found that only [14 percent of audited covered entities were substantially fulfilling their risk analysis responsibilities](https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/audit/2016-2017-hipaa-audits-industry-report/index.html). The other 86 percent were either failing entirely or doing it so poorly that it did not meet the regulatory standard.

A significant share of the failing population had done a risk analysis at some point. The problem was that the analysis was years out of date and did not reflect the current environment. New EHR. New telehealth platform. New cloud backup vendor. New medical device. New satellite office. None of it captured in the risk analysis on file. The Security Rule does not specify a fixed cadence for risk analysis updates, but [HHS guidance](https://www.hhs.gov/hipaa/for-professionals/security/guidance/guidance-risk-analysis/index.html) is clear that the analysis must be updated when there are material changes to the environment, and that periodic re-evaluation is expected as a matter of ongoing compliance.

[BayCare Health System](https://www.hhs.gov/press-room/hhs-ocr-hipaa-agreement-baycare.html) paid $800,000 in May 2025 after OCR found that a former employee had used valid credentials to access patient records months after termination. The risk analysis on file did not reflect the current state of access controls or the workforce offboarding process. The corrective action plan requires BayCare to conduct a comprehensive risk analysis, develop a responsive risk management plan, and review and revise its access control practices. That is OCR's standard remedy when the analysis exists on paper but does not match operational reality.

The fix is to schedule risk analysis updates as a recurring program activity, not a project. At minimum, the analysis should be reviewed annually and refreshed any time there is a material change to the environment: new technology, new locations, new contracts, mergers and acquisitions, significant workforce changes, or significant changes to clinical workflows. The review should be documented even when no material changes have occurred, so that the file shows continuous attention. A risk analysis dated three years ago with no review history is functionally equivalent to no risk analysis at all in front of an investigator.

## What to do this week

Six concrete actions:

1. **Find the most recent risk analysis on file.** If you cannot find one, you have your answer. If you can find one, check the date. If it is older than 12 months and your environment has changed since, it needs to be refreshed.

2. **Compare it to NIST SP 800-66 Rev 2.** That document is HHS's recognized methodology for HIPAA risk analysis. If your analysis does not roughly map to the structure described in 800-66 (asset inventory, threat identification, vulnerability identification, likelihood and impact assessment, control evaluation, residual risk), it is probably a gap assessment in disguise.

3. **Pull your asset and ePHI inventory.** Walk through it room by room and system by system. Note anything that holds, transmits, or could touch ePHI that is missing. Update the inventory to reflect reality.

4. **Cross-check against your BAA list.** Every business associate that handles your ePHI should appear in both the BAA file and the asset inventory. Gaps in either direction are findings waiting to be made.

5. **Verify there is a risk management plan that ties to the risk analysis.** Every identified risk should have an owner, a treatment decision, a control description, and a status. If there is no plan or the plan is disconnected from the analysis, you have the second mistake on this list.

6. **Schedule the next review.** Put it on the calendar. Assign an owner. Put it in the policy. The single biggest predictor of whether a practice will be in compliance two years from now is whether anyone owns the ongoing maintenance of the risk analysis.

The OCR Risk Analysis Initiative is not slowing down. The settlements continued through both administrations. The amounts have ranged from a few thousand dollars for very small practices to seven figures for larger ones. Every one of them shares the same root cause and the same fix. The fix is unglamorous, and it is also the single most cost-effective HIPAA compliance investment a regulated entity can make.

Practices that take the risk analysis seriously avoid the fines, build a defensible compliance posture, and are dramatically better positioned when an actual incident occurs. Practices that do not are showing up in OCR press releases.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB supporting healthcare, defense, federal, and commercial organizations through HIPAA, CMMC, NIST 800-171, and FedRAMP compliance engagements. Questions about HIPAA risk analysis methodology, OCR audit preparation, or breach response can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*
