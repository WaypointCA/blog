---
title: "Aerospace Suppliers Are Governed by Two Rule Sets That Do Not Agree"
date: 2026-08-12
draft: true
tags: ["Aerospace", "Space Systems", "ITAR", "NIST 800-171", "CUI", "CNSSI 1253", "Defense"]
categories: ["Compliance", "Defense"]
summary: "A NIST 800-171 environment can be fully compliant and still be an ITAR violation, because the two regimes ask different questions about the same data. Add national security space requirements and you have three overlapping rule sets on one server room."
author: "Cameron Hopkin"
---

Most compliance advice for aerospace suppliers is defense contractor advice with the word aerospace pasted on top. It walks you through CUI scoping and NIST 800-171 and stops there, as though a company machining parts for a launch vehicle faces the same problem as a company writing software for the Army.

It does not, and the difference is not a matter of degree. Aerospace sits at the intersection of at least two regulatory regimes that were written by different people, for different reasons, and that ask fundamentally different questions about the same file sitting on the same server. If you are supporting national security space programs, there is a third.

You can be fully compliant with one and in violation of another. That is the part nobody tells small suppliers until something goes wrong.

## The two questions

**NIST 800-171 asks: is this data protected?**

Under DFARS 252.204-7012, if you handle covered defense information you implement the 110 requirements and safeguard the data. The controls care about encryption, access control, audit logging, boundary protection, and incident response. The regime is fundamentally about the *state* of the data and the system holding it.

Nothing in NIST 800-171 asks about the citizenship of the person with access. An engineer is an authorized user or is not, and the control set is indifferent to their passport.

**ITAR asks: who can see this, and are they a US person?**

If your technical data relates to a defense article on the United States Munitions List, the International Traffic in Arms Regulations apply, and their central concern is *who*. Access by a foreign person, even a foreign person lawfully employed by you, standing in your building, on your network, is an export. It is called a deemed export, and it requires authorization the same as shipping the part overseas would.

ITAR is largely indifferent to whether your encryption is FIPS-validated, except where that specifically matters. NIST 800-171 is entirely indifferent to nationality. Each regime is silent exactly where the other is loudest.

## Where this actually bites

Here are the situations I see cause real problems, none of them exotic.

**The offshore managed service provider.** A supplier hires an MSP for after-hours coverage. The MSP is competent, the contract is sound, the security posture is arguably better than what the supplier ran alone. The MSP staffs its night shift from outside the United States. Those administrators have domain access to systems holding ITAR technical data. From an 800-171 standpoint this is fine, and privileged access is logged and controlled. From an ITAR standpoint the company has been committing unauthorized exports on a nightly basis, and every one of those nights is separately actionable.

**The cloud tenancy that is in the right region and the wrong hands.** Moving to a government cloud region solves data residency. It does not automatically solve personnel. The question is not only where the data sits but who at the provider can reach it and under what controls. ITAR has an encryption carve-out that makes properly implemented end-to-end encryption a workable path, and it has specific conditions that have to actually be met rather than assumed.

**The engineer who is a green card holder, and the one who is not.** US person status under ITAR includes lawful permanent residents. It does not include everyone lawfully authorized to work in the United States. A supplier that treats work authorization and US person status as the same thing has an access control model that quietly does not match its export obligations, and HR systems generally do not track the distinction the regulations need.

**The CUI enclave that solves the wrong problem.** Enclave architecture is the right answer for 800-171 scoping, and I recommend it constantly. But an enclave scoped by *data sensitivity* while access is granted by *job function* will hand ITAR technical data to whoever needs the engineering share. Scope shrinks the assessment boundary. It does not by itself implement nationality-aware access control.

The pattern in all four is the same. Controls designed to answer one regime's question do not answer the other's, and passing an audit against one framework produces no evidence at all about the other.

## Where CMMC currently sits

Since this is the question every aerospace supplier asks first: DoD suspended CMMC Phase 2 third-party certification in July 2026 and paused DIBCAC assessments during the program review.

Your DFARS 252.204-7012 obligations did not change, your NIST 800-171 implementation is still required, and your SPRS score is still a legal statement you affirm. I wrote about what the suspension actually means, and why it raises your False Claims Act exposure rather than lowering it, in [CMMC Phase 2 Is Suspended. Your Legal Exposure Went Up.](https://blog.waypointca.com/posts/cmmc-phase-2-suspended-self-reporting-risk/)

For aerospace specifically, the suspension changes nothing about ITAR. Export control was never part of the CMMC program and has its own enforcement path through the State Department's Directorate of Defense Trade Controls, with penalties that make most cybersecurity findings look modest.

## The third regime: national security space

If your work supports national security space missions, the requirements stack again.

CNSS Policy No. 12 and CNSSI 1200 set information assurance requirements for the procurement of space systems supporting national security missions. Systems categorized as national security systems come in under CNSSI 1253 rather than the NIST 800-53 baselines most people know, with its own control selection process and overlays. DoDI 8581.01 applies related principles across DoD space programs.

This is genuinely different work, and I want to be precise about why. CNSSI 1253 is not simply 800-53 with more controls. The categorization process differs, the overlays carry program-specific tailoring, and the assessment expectations assume a maturity that most commercial suppliers have not built. The scale difference is measurable: one Aerospace Corporation analysis counted roughly 389 controls in a CNSSI 1253 Moderate baseline against 262 in the comparable NIST 800-53 baseline. Treat exact counts as version-dependent, the way you should treat any baseline number, but the delta is real and it lands on top of categorization logic that does not transfer from civilian work. Teams that have done FedRAMP or FISMA work often assume the experience carries over cleanly. Some of it does. The categorization and overlay logic does not.

I led the first CNSSI 1253 assessment for the ULA Vulcan program as cybersecurity architect over a 28-person team, running concurrently with DCMA and ISO recertification, and closed it with zero audit findings. The thing I would tell any supplier entering this space is that the assessment is not the hard part. Establishing repeatable evidence and policy management that survives the assessment and keeps producing afterward is the hard part, and it is what determines whether the second year costs a fraction of the first or the same again.

For commercial space rather than national security work, the landscape is advisory rather than mandatory so far. Space Policy Directive 5 established cybersecurity principles for space systems in 2020. NIST has published IR 8270 for commercial satellite operations, IR 8401 for the satellite ground segment, and IR 8441 for hybrid satellite networks. CISA has published recommendations for space system operators. None of these carry the force of a contract clause today. All of them are the obvious source material for whatever does eventually become mandatory, and operators who align early will not be rewritten later.

## The shop floor problem is worse in aerospace

One more thing specific to this industry. Aerospace manufacturing runs operational technology that predates every framework in this post: CNC machines, PLCs, coordinate measuring machines, test stands, and cell controllers running operating systems no longer receiving patches.

That equipment is in scope, it is frequently the least defensible part of the environment, and it holds or transmits exactly the technical data both regimes care about. A CNC controller with the toolpath for an ITAR-controlled part on its local drive is an export control asset that happens to also be a machine tool. I wrote about the operational technology scoping trap for Florida manufacturers in [Florida Makers and the OT Blind Spot](https://blog.waypointca.com/posts/florida-makers-cmmc-ot/), and everything in it applies with more force when export control is in play.

## What to do

1. **Map your data by regime, not by sensitivity.** Build one inventory that tags each repository with whether it holds CUI, ITAR technical data, both, or neither. Most suppliers have never produced this, and it is the artifact that makes every subsequent decision tractable.

2. **Audit privileged access for US person status specifically.** Every administrator, every MSP, every contractor, every cloud support path. Ask the nationality question explicitly, because your identity provider does not track it and your HR system probably tracks work authorization instead.

3. **Read your MSP contract for offshore support.** Follow-the-sun coverage is a common and often unadvertised delivery model. Ask directly where night shift sits.

4. **Design access control to answer both questions.** Sensitivity determines the control set. Nationality determines the access list. A model implementing only the first will satisfy an 800-171 assessor and will not survive an export control review.

5. **Keep implementing 800-171 on the current schedule.** The certification requirement is suspended. The contract clause is not, and a defensible SPRS score is the thing you are actually affirming.

6. **If you are entering national security space work, plan for CNSSI 1253 as a distinct effort.** Budget it separately from your CUI program. The categorization and overlay work does not fall out of a 800-171 project, and treating it as an increment is how schedules slip.

## The honest read

Aerospace suppliers get told they have a cybersecurity problem. What they usually have is a data governance problem wearing a cybersecurity costume. The controls are largely the same ones everyone else implements. What differs is that you have to answer two questions simultaneously, and the frameworks each answer only one.

The suppliers who handle this well stop treating export control as the legal department's concern and cybersecurity as IT's concern. They are two views of one question, which is who is allowed to see this and how do you prove it. Build one access model that answers both and the audits get straightforward. Run them as separate programs and you will keep passing one while quietly failing the other.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB supporting defense, aerospace, federal, healthcare, and state organizations through NIST 800-171, DFARS, FedRAMP, and HIPAA compliance engagements. Our founder led the first CNSSI 1253 assessment for the ULA Vulcan program with zero audit findings. Questions about CUI and export control overlap, CNSSI 1253 readiness, or OT scoping can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*

*This post describes regulatory obligations in general terms and is not legal advice. Export control determinations are fact-specific. Consult qualified export control counsel on classification and licensing questions.*
