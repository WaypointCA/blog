---
title: "Florida Gave You the Mandate, Vetoed the Safe Harbor, and Just Funded the Fix"
date: 2026-08-11
lastReviewed: 2026-08-11
draft: false
tags: ["Florida", "State Government", "NIST CSF", "Local Government", "Ransomware", "Compliance"]
categories: ["State"]
summary: "Florida is one of the few states that mandates a cybersecurity framework by statute. The alignment deadlines have already passed, the liability safe harbor was vetoed, and as of July 1 there is finally state money on the table. Here is what actually applies to Florida agencies, counties, and cities."
author: "Cameron Hopkin"
---

Most states handle government cybersecurity through guidance. A best practices document, a voluntary maturity model, an annual survey nobody reads. Florida went a different way. It put a framework requirement in statute, attached reporting deadlines measured in hours, and made one common incident response option illegal.

Then it vetoed the bill that would have given you liability cover for complying, and two years later funded a grant program to help you pay for it.

If you run IT for a Florida county, city, special district, or school board, that combination is the environment you are operating in right now. It is more demanding than most local officials realize and better resourced than it was six weeks ago.

## What is actually binding

The [Local Government Cybersecurity Act](https://www.flsenate.gov/Session/Bill/2022/7055), created by HB 7055 in 2022 and codified at Florida Statutes 282.3185, is the operative law for counties and municipalities. State agencies sit under 282.318. The local government provisions are the ones getting ignored, so start there.

**Framework alignment is not optional.** Local governments were required to adopt cybersecurity standards consistent with best practices, including the NIST Cybersecurity Framework, and the deadlines were tiered by entity type. Counties with populations of 75,000 or more and municipalities with populations of 25,000 or more had until January 1, 2024. Smaller counties and municipalities had until January 1, 2025. The statute also requires each local government to notify the Florida Digital Service of its compliance, and FLDS runs an online attestation form for exactly that purpose, which matters later in this post.

Both dates have passed. That is worth sitting with for a moment, because in my experience talking to small Florida jurisdictions, a meaningful share of them are not aligned, and some are not aware the requirement exists.

**Ransomware incidents get 12 hours.** A ransomware incident must be reported to the Cybersecurity Operations Center, the Cybercrime Office of the Florida Department of Law Enforcement, and the local sheriff, no later than 12 hours after discovery.

Twelve hours is a genuinely short clock. It is shorter than the 72 hours federal contractors get under DFARS. If your incident response plan does not name the people who make that call and give them the contact paths in advance, you will spend a meaningful fraction of the window figuring out who to call, during the worst morning of your year.

**Other serious incidents get 48 hours.** Cybersecurity incidents the local government determines to be severity level 3 or higher must be reported as soon as possible, and no later than 48 hours after discovery. Lower-severity incidents can be reported voluntarily, and the severity determination is yours to make and defend, which is its own reason to have a rating methodology written down before you need it.

**You cannot pay.** Under 282.3186, a county or municipality experiencing a ransomware incident may not pay or otherwise comply with a ransom demand. Public funds cannot be used for ransom payments.

Read that as an architecture requirement, not a policy statement. If paying is off the table by law, then your recovery capability is the only path back, and untested backups are not a recovery capability. Every Florida local government should be able to answer, with a date, when it last restored a production system from backup as an exercise rather than as an emergency.

## The safe harbor that vendors keep telling you about

Here is where a lot of published advice goes wrong, including advice you may have been given by people selling you something.

In 2024 the Legislature passed [HB 473](https://www.flsenate.gov/Session/Bill/2024/473), the Cybersecurity Incident Liability Act. It would have given covered entities an affirmative defense against data breach claims if they maintained a program substantially complying with a recognized framework, NIST CSF among them. It passed the House 81 to 28 and the Senate 32 to 8.

Governor DeSantis vetoed it on June 26, 2024.

There is no Florida cybersecurity safe harbor. Ohio has one. Connecticut has one. Florida does not, and no equivalent has been enacted since. I still see consultants and MSPs citing HB 473 in sales material as though it were law, sometimes in documents dated this year.

The practical consequence is uncomfortable and worth stating plainly. Florida imposes the obligations without offering the corresponding liability protection. You carry the mandate and the exposure. Aligning to NIST CSF is still the right thing to do, and it will still help you enormously in litigation as evidence of reasonable care. It just is not the statutory shield the vetoed bill would have created, and you should not let anyone plan your budget as though it were.

## The part that is actually new

On May 22, 2026, the Governor signed [HB 1085](https://www.flsenate.gov/Session/Bill/2026/1085) into law as Chapter 2026-115. It took effect July 1, 2026.

The bill creates a Local Government Cybersecurity Protection Program inside the Florida Digital Service, codified at section 282.31855. The Digital Service is directed to enter data sharing agreements with local governments, administer a grant program providing IT commodities and services for cybersecurity purposes, contract for and award IT resources to participating local governments, and report to the Governor's Office of Policy and Budget and legislative appropriations chairs. Note the mechanism: under the state's existing local government grant program, FLDS has procured cybersecurity solutions directly on behalf of awardees rather than cutting checks, and the new program is built the same way. You will not be handed money to figure out how to spend. You will be handed capabilities against a defined need, which is one more reason the defined need has to exist on paper first.

It passed 109 to 0 and 104 to 1 in the House, and 37 to 0 and 39 to 0 in the Senate. Unanimous is rare and it tells you something about how the Legislature now views the risk profile of Florida's roughly 400 municipalities, many of which run IT on a headcount you could count on one hand.

For a small jurisdiction, this is the first time the state has offered to help carry the cost rather than simply setting the requirement. If you are a city of 8,000 that has been deferring this because the budget was never there, the budget conversation changed six weeks ago and most of your peers have not noticed yet.

Two practical notes. Programs like this reward the applicant who arrives with an assessment already in hand, because a documented gap list is a fundable project and a vague sense of concern is not. And grant programs administered through a state agency tend to allocate on a first-qualified basis rather than a most-deserving one.

## Why Florida specifically

Florida's exposure is not generic, and neither is its history.

Riviera Beach paid roughly $600,000 in ransom in 2019. Lake City paid about $460,000 the same month. Those two incidents are a meaningful part of why 282.3186 exists at all. The Legislature watched Florida cities wire money to criminals and removed the option.

The state also has an unusual concentration of the things attackers like: a very large retiree population, which means an unusual density of healthcare providers and the protected health information they hold, hundreds of small municipalities and special districts with minimal IT staffing, a large tourism and hospitality payment card footprint, and a defense and aerospace corridor running from Jacksonville through the Space Coast to Eglin.

That last one matters because the requirements stack. A Space Coast machine shop can simultaneously be a Florida business under state law, a defense subcontractor under DFARS 252.204-7012, and a handler of export-controlled technical data. Those are three different rule sets applied to the same server room.

## What to do

1. **Determine your actual tier and find your attestation.** Counties check against the 75,000 threshold, municipalities against 25,000, and either way your deadline has passed. The statute required you to notify the Florida Digital Service of compliance through its attestation process, so this is a records check, not a research project. If nobody in your building can produce the attestation, you have your answer.

2. **Time your 12-hour clock.** Not the plan. The clock. Who declares a ransomware incident, who contacts the Cybersecurity Operations Center, FDLE Cybercrime, and the sheriff, and where those numbers live when email is down. Run it as a tabletop and record how long it actually took.

3. **Prove your recovery, since paying is illegal.** Restore a production system from backup on a normal Tuesday and write down the date and the elapsed time. If that exercise has never happened, your ransomware plan is a document rather than a capability.

4. **Get a NIST CSF 2.0 gap assessment done before you apply for grant money.** The assessment is what converts "we need cybersecurity help" into a scoped, costed, fundable project. It also happens to be the thing the statute asks you to align to.

5. **Stop planning around a safe harbor that does not exist.** If a vendor proposal cites HB 473, ask them when it was signed. Then consider what else in the proposal was not checked.

6. **If you are a private Florida business, look at which regimes stack on you.** State obligations, HIPAA if you touch PHI, DFARS if you are anywhere in the defense supply chain, PCI DSS v4.0.1 if you take cards. The compliance program that treats these as one program with overlapping controls costs dramatically less than four programs run in parallel.

## The honest read

Florida asked local governments to do something real, gave them a hard deadline, removed their worst option, declined to give them liability cover for compliance, and has now, finally, offered to help pay.

Three of those four are constraints. The fourth is an opportunity with a fresh effective date and very little competition for attention so far. The jurisdictions that get assessed this quarter will be the ones with a fundable project on the desk when the program starts allocating.

The deadline already passed. The money just showed up. Those two facts together should tell you what the next ninety days are for.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB and a registered MyFloridaMarketPlace vendor and certified Florida Veteran Business Enterprise, based in DeLand. We support Florida agencies, counties, municipalities, and districts with NIST CSF 2.0 assessments, security program development, and incident response planning. Questions can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*

*This post describes statutory requirements in general terms and is not legal advice. Consult your county or city attorney on how these provisions apply to your jurisdiction.*
