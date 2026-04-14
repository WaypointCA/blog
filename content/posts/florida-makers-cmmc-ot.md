---
title: "Florida Makers and CMMC: The OT Blind Spot on Your Shop Floor"
date: 2026-04-14
draft: false
tags: ["CMMC 2.0", "OT Security", "Manufacturing", "NIST 800-171", "Defense", "Florida"]
categories: ["Compliance", "Manufacturing"]
summary: "Your CNC machines, PLCs, and IoT sensors are in scope. The question of whether g-code from a CUI drawing is itself CUI is one of the most contested questions in the CMMC manufacturing world. Here is the defense plan that holds regardless of which reading your assessor brought with them."
author: "Cameron Hopkin"
---

Most small Florida manufacturers have not had the CMMC scoping conversation yet. Their assessor will make them have it.

The single most contested question in the CMMC manufacturing world right now is whether g-code generated from a CUI drawing is itself CUI. One camp, pointing to the NARA CUI Marking Handbook and the derivative document rules, argues that any file incorporating, paraphrasing, or restating CUI from an authorized source inherits the markings of the source. Another camp, including credible SMB manufacturing voices, argues that g-code is the shop's own work product, that it encodes machine instructions rather than the protected technical data itself, and that treating it as CUI over-expands scope in a way the rule never intended.

Both camps have real arguments. Both cite real authority. Neither side has won the debate publicly, and none of the 80-plus authorized C3PAOs have issued unified guidance on the question. Which means on November 10, 2026, when [Phase 2 enforcement begins](https://blog.waypointca.com/posts/cmmc-level-2-small-business/), the answer an individual Florida shop gets will depend substantially on which assessor walks through the door.

The shop that wins its assessment is not the shop that picks a side. It is the shop that has a documented, defensible scoping position that survives either interpretation, backed by primary sources and written into the SSP before the assessor arrives. That is the defense plan. That is also the gap I see in the field.

This post walks through what is actually contested, what is settled, and how to build a scoping position that holds regardless of which interpretation your assessor brought with them that morning.

## What actually counts as operational technology in a shop

Before getting into the scoping debate, it helps to be precise about what we are even talking about. "OT" is one of those acronyms that sounds technical but covers a much wider footprint than most people realize.

Operational technology is hardware and software that directly monitors or controls the physical environment. In a manufacturing context that includes:

- **CNC machine controllers** running Fanuc, Siemens, Heidenhain, Mazak, Haas, or any of the other dozen control systems on a typical shop floor.
- **Programmable Logic Controllers (PLCs)** from Allen-Bradley/Rockwell, Siemens, Mitsubishi, Omron, and others. CompactLogix and Micro850 devices are particularly common in small manufacturing shops, and they are currently being [actively targeted by Iranian-affiliated threat actors](https://www.cisa.gov/news-events/cybersecurity-advisories/aa26-097a) using internet-exposed configuration software to reach them.
- **Human Machine Interfaces (HMIs)** running on Windows boxes that often cannot be patched without revalidating the entire production system. Many of these are running operating systems Microsoft stopped supporting years ago.
- **SCADA and historian servers** that aggregate production data and let supervisors see what is happening across the shop.
- **Industrial IoT sensors** measuring temperature, pressure, vibration, machine tool wear, energy consumption, and feeding it back to a manufacturing execution system.
- **Coordinate measuring machines (CMMs)** and other quality inspection equipment that compares finished parts against design specs.
- **Building automation and access control systems** that connect to the same network as everything else.
- **Vendor remote access pathways** that machine OEMs use for diagnostics and software updates.
- **Engineering workstations** running CAM software that translates CAD models into the instructions that get sent to the CNC.

Note the last item. Engineering workstations are not OT, but they are the bridge between CUI and OT. They are often the first place an assessor will challenge your scope, because they are where the CUI part drawing becomes the input to whatever the shop produces next.

## The Specialized Asset rule that everyone misreads

CMMC defines five asset categories in [32 CFR §170.19(c)(1) Table 3](https://www.ecfr.gov/current/title-32/subtitle-A/chapter-I/subchapter-G/part-170/subpart-D/section-170.19): CUI Assets, Security Protection Assets, Contractor Risk Managed Assets, Specialized Assets, and Out-of-Scope Assets.

Specialized Assets is the category where OT, IIoT, GFE, restricted information systems, and test equipment all live. The official [DoD CMMC Level 2 Scoping Guide](https://dodcio.defense.gov/Portals/0/Documents/CMMC/ScopingGuideL2v2.pdf) describes them as assets that "may or may not process, store, or transmit CUI" but cannot be fully secured to the standard NIST 800-171 controls because of legitimate operational or technical constraints.

Here is what most contractors hear when they read that: "Specialized Assets are out of scope. I do not have to assess my CNC machines."

Here is what the rule actually says: Specialized Assets that process, store, or transmit CUI are **in scope**. They must appear in your asset inventory. They must be documented in your System Security Plan. They must show up on your network and data-flow diagrams. The assessor will verify they are identified, that their function is documented, and that risk-based safeguards are in place. The assessor is not going to walk through all 110 NIST 800-171 controls against a 1998 PLC, but they are going to verify that you have thought about the asset, isolated it, and have a defensible story for how you protect it.

The relief from the full control set is a recognition that you cannot run modern endpoint protection on a Fanuc controller. It is not a recognition that the controller does not exist for compliance purposes.

## The contested question, and what is actually settled

The derivative document rule is real. The [NARA CUI Marking Handbook](https://www.archives.gov/files/cui/20161206-cui-marking-handbook-v1-1.pdf) is explicit: derivative classification for CUI involves "incorporating, paraphrasing, restating, or generating in new form" CUI from an authorized source, and the resulting document inherits the markings. The [DoD CUI Registry](https://www.dodcui.mil/CUI-Categories-and-Abbreviations/) defines Controlled Technical Information as technical data with military or space application that is subject to controls on access, use, reproduction, modification, performance, display, release, disclosure, or dissemination.

The question is whether g-code meets the bar. A reasonable assessor can argue it both ways.

**The "g-code is derivative CUI" reading:** A part drawing with dimensions, tolerances, and material callouts is the source CUI. The CAM process incorporates those specific values into a machine-executable program. The resulting g-code file contains the same protected technical information in a different format. Under 32 CFR 2002.4(h) and the NARA derivative rule, the new document inherits the markings of the source. The CNC controller storing that file is therefore a Specialized Asset that processes CUI and is in the CMMC Assessment Scope under 32 CFR 170.19(c)(1).

**The "g-code is machine instructions, not CUI" reading:** The shop owns the toolpath. The machinist made design decisions about approach angles, feed rates, tool selection, and sequencing that are not present in the source drawing. The g-code is the shop's own work product. It is machine instructions, not a restatement of the technical data package. The source CUI remains CUI and gets protected on the engineering workstations. The derived file is a production artifact that should be protected as proprietary business information, not elevated to CUI status by implication.

Both readings are internally consistent. Both can be defended with primary sources. And right now, neither the DoD CIO, the Cyber AB, nor any court has issued binding guidance that would resolve it for every shop.

What is settled, and what every Florida manufacturer should write into their SSP regardless of the g-code debate:

**Engineering workstations running CAM software are CUI Assets.** These machines open the CUI part drawing, load it into CAM, and produce derivative output. They are unambiguously in scope under any reading of the rule. They must meet the full 110 NIST SP 800-171 Rev 2 controls. This is not debatable.

**The network segment connecting the CAM workstation to the CNC controller is in scope** as a Security Protection Asset or a controlled data flow. Whether the destination is classified as CUI or not, the path exists, it crosses a boundary, and it has to be documented in the network diagram. An assessor who sees an uncontrolled path from a CUI workstation to any other system will write a finding.

**Vendor remote access pathways to shop floor equipment are in scope.** Machine OEM diagnostic tunnels, cellular modems for remote service, and any inbound path to a PLC or HMI is either a Security Protection Asset or a contractor risk that has to be mitigated with logging, MFA, and scheduled access. The CISA, FBI, and NSA advisory on Iranian-affiliated targeting of internet-exposed Rockwell Automation PLCs makes clear that this is a real active threat, not a theoretical one.

**Specialized Assets are not out of scope.** Whatever you decide about g-code, the Specialized Asset category under 32 CFR 170.19(c)(1) requires inventory, SSP documentation, network diagram placement, and compensating controls. The "limited assessment" language means the asset is not evaluated against all 110 controls. It does not mean the asset is ignored. Any shop telling its assessor "the CNCs are Specialized, so they're out of scope" is going to have a bad day.

**The False Claims Act exposure is the same either way.** A shop that misrepresents its scope in SPRS, then has the scope challenged by a C3PAO, then ends up with a contract eligibility gap, has the same FCA problem whether the underlying dispute was about g-code or about anything else. [MORSECORP paid $4.6 million](https://www.justice.gov/opa/pr/defense-contractor-morsecorp-inc-agrees-pay-46-million-settle-cybersecurity-fraud) and [Raytheon paid $8.4 million](https://www.justice.gov/opa/pr/raytheon-companies-and-nightwing-group-pay-84m-resolve-false-claims-act-allegations-relating) in cybersecurity-related False Claims Act settlements, neither of which was triggered by a breach. Both were triggered by the accuracy of the compliance claim itself.

## Building a defensible scoping position

The shops that will pass their assessments, regardless of which interpretation their assessor holds, do five things before the assessor arrives.

**1. Document the scoping rationale in the SSP with primary-source citations.** Whatever your position on g-code, write it down. Explain the reasoning. Cite 32 CFR 170.19, the NARA CUI Marking Handbook, the CTI category definition from the DoD CUI Registry, and your contract's DFARS 252.204-7012 clause. An assessor who disagrees with your position but sees that you have made a documented, defensible decision with real sources is in a different negotiating posture than an assessor who sees no documentation at all. The written rationale is what separates a scoping disagreement from a scoping failure.

**2. Treat the engineering bridge as a CUI enclave no matter what.** The CAM workstation, the file share where drawings live, the intermediate storage, the person who does the CAM work — all of it gets the full NIST SP 800-171 Rev 2 treatment. MFA, FIPS-validated encryption at rest and in transit, audit logging, least privilege, application allowlisting. Even if you later argue the g-code is not derivative CUI, the source drawing absolutely is, and the environment that handles it cannot be compromised by debate.

**3. Implement compensating controls on the shop floor that hold under either reading.** Network isolation between the office and shop floor VLANs. No inbound internet access to CNC controllers, PLCs, or HMIs. Vendor remote access only through a logged jump host with MFA, never a permanent OEM tunnel. Physical access controls on production equipment. Configuration baselines and drift detection. None of these controls depend on whether g-code is CUI. All of them are defensible independently, and all of them show the assessor that the shop has taken the OT security question seriously.

**4. Build a data flow diagram that shows exactly where CUI enters, who touches it, and where every derived work product goes.** The diagram is the single most effective piece of documentation in a scoping dispute. When an assessor asks "where does CUI live in your environment," the right answer is not a verbal walkthrough. It is a labeled diagram with asset categories, boundaries, and data flows annotated against the source drawing. An assessor with a g-code-is-CUI position will point at the diagram and agree that the engineering workstation is a CUI Asset, then move on. An assessor with a g-code-is-not-CUI position will point at the diagram and agree that the CNC is a Specialized Asset with compensating controls, then move on. Either way the debate resolves in minutes instead of hours because the diagram told the story.

**5. Prepare the compensating-control story for the CNC network in writing.** The contested assets need a prepared answer to the question "how is CUI protected on this device." That answer cites the network segmentation, the access controls, the vendor governance, the configuration management, and the monitoring. It does not depend on the derivative CUI debate. It stands on its own as a reasonable interpretation of how to apply NIST SP 800-171 Rev 2 to an OT device that cannot run modern endpoint protection. The SSP documents it, the network diagram shows it, and the evidence repository proves it.

These five artifacts together are the defense plan. Not a declaration of where g-code falls in the CUI category. A documented, sourced, defensible position that holds regardless of which way a specific assessor interprets an unresolved debate.

## Why this is particularly painful for Florida manufacturers

Florida is a top-five state for DoD contract spending. The state's manufacturing sector employs [over 465,000 people across roughly 11,656 companies](https://www.industryselect.com/blog/top-10-manufacturing-companies-in-florida), and the I-4 corridor between Tampa and the Space Coast is one of the densest defense manufacturing clusters in the country. Lockheed Martin in Orlando. L3Harris in Melbourne and Palm Bay. Northrop Grumman in Melbourne. Raytheon's Florida footprint. The Eglin Air Force Base munitions ecosystem in the panhandle. The whole space launch supply chain on the east coast.

Underneath those primes is a long tail of tier-three and tier-four subcontractors. Machine shops with 15 employees making bracket assemblies for missile guidance systems. Specialty platers and finishers. Composite fabricators. Cable harness builders. Electronics assemblers. Most of them are family-owned, most of them are running shop floor equipment that was installed before "cybersecurity" was even a department in any company, and most of them have an IT setup that consists of QuickBooks, an email server somewhere, and a shared drive on a NAS that lives in a closet.

These shops have been getting away with cybersecurity neglect for years because nobody was checking. CMMC is what changes that. The annual senior-officer affirmation in SPRS is a legally significant statement. The C3PAO assessment in Phase 2 is a real audit by a real assessor who will look at real shop floor equipment.

The state of Florida is not blind to this. [FloridaMakes](https://www.floridamakes.com), the state's official representative of the NIST Manufacturing Extension Partnership, has been working on cybersecurity awareness for the manufacturing sector for years. In August 2024, FloridaMakes [partnered with Cyber Florida at USF](https://cyberflorida.org/floridamakes-partnership-announced/) to expand cybersecurity assessment capabilities specifically for Florida manufacturers and DIB companies. The infrastructure to help Florida manufacturers get this right exists. The bottleneck is awareness and time.

The time bottleneck is real. There are roughly [80 to 100 authorized C3PAOs](https://cyberab.org/Catalog/Certified-Assessors-and-Instructors/Certified-Third-Party-Assessor-Organizations) for an estimated 80,000 organizations needing Level 2 certification. Current capacity is roughly one assessment per C3PAO per month, and many are already booked through the end of 2026. Multiple industry analysts are predicting that 33,000 to 44,000 companies, 15 to 20 percent of the entire defense industrial base, will exit the DoD market between 2025 and 2027 because they cannot complete CMMC compliance in time. The exits will concentrate in exactly the kind of small machine shops Florida is full of.

The Florida manufacturers who survive this transition are the ones who started early, scoped honestly, documented their scoping rationale with primary sources, and built shop floor security architectures that match the reality of how parts actually get made.

## The architecture that actually works

The good news is that the technical solution is well understood. The challenge is operational discipline, not invention.

**Step one: find the CUI first.** Before you touch a single piece of equipment, walk the workflow. Where do drawings come in? Email? Customer portal? File sync? Once they arrive, where do they go? Whose workstation? Which file share? Which CAM seat? Which controller? Which inspection program? Which shipping document? Map it on paper. Then map it again to make sure you got it right. Most small shops discover during this exercise that CUI is in three or four places they did not know about, including a personal Dropbox account that an engineer set up in 2019 to share files with a colleague who has since left.

**Step two: segment the shop floor network.** This is the architectural foundation. The OT network has to be a separate broadcast domain from the office network, with a clearly defined boundary, documented connections crossing the boundary, and inspection of any traffic between zones. CISA's guide to [segregating ICS-OT architecture](https://www.cisa.gov/sites/default/files/2023-03/Segregating%20the%20ICS-OT%20Insecure%20by%20Design%20Architecture%20508c%20Rev%20E%20.pdf) walks through the Purdue-style zone model at each level. You do not have to implement Purdue perfectly to get value from it. You do have to know which devices live at which level and what traffic is allowed to cross the boundaries.

For most small shops, this means installing a firewall between the office network and the shop floor network, putting the CNCs and PLCs on their own VLAN with no inbound internet access, and treating any cross-zone traffic (engineering workstation pushing a file, MES collecting machine status) as a controlled and logged data flow.

**Step three: isolate the engineering bridge.** The engineering workstations that translate CUI drawings into machine instructions are the highest-value targets in this whole architecture. They handle CUI directly, they have outbound network access to controllers, and they are usually running Windows with full internet connectivity. Treat them like servers. No personal use. Application allowlisting. Disk encryption. MFA on login. Minimum privilege. Regular patching. Centralized logging. If you can put them inside a CUI enclave with strict egress to the shop floor, do it. If you cannot, at least make them the most-controlled workstations in the building.

**Step four: deal with the legacy controllers honestly.** A 2002 PLC running Windows XP with proprietary firmware cannot run modern endpoint protection. That is a fact. The CMMC rule acknowledges this fact by giving you a Specialized Asset path that does not require full 800-171 compliance. What it requires instead is a documented set of compensating controls. For most small shops the working set looks like:

- Network isolation (the controller is on a segment with no internet access and only the specific protocol ports it needs).
- Physical access control (the controller is in a locked enclosure or a restricted shop area).
- Vendor access governance (any remote access is via a VPN to a jump host with logging, not a permanent OEM tunnel into the device).
- Configuration baseline documentation (you know what good looks like and you can detect changes).
- Monitoring at the network boundary (you can see if the controller starts talking to something it should not).
- Patching when possible during scheduled maintenance windows, and a documented decision to not patch when not possible, with the residual risk acknowledged in the SSP.

None of this requires running antivirus on the controller itself. All of it has to be written down and provable.

**Step five: document everything in the SSP.** The CMMC assessor is going to ask for your System Security Plan and walk through the asset inventory. Every Specialized Asset has to be in there. Every CUI workflow has to be traceable on the data flow diagram. Every compensating control has to have a rationale. The SSP is not a marketing document. It is the artifact that demonstrates you have actually done the engineering work.

**Step six: build a maintenance discipline.** Compliance is not a project, it is a function. The shop floor changes. New machines come in. Old machines get replaced. Vendors push firmware updates. Operators leave and new ones get hired. The asset inventory has to be updated as those changes happen, the SSP has to track reality, and the SPRS score has to be re-affirmed annually by a senior officer who is putting their name on a legal statement. If your shop has nobody whose job description includes "maintain the CMMC compliance posture," you are going to drift out of compliance within a year.

## Seven things to do this month

For the small Florida manufacturer reading this and realizing the scoping conversation is coming:

1. **Do a CUI inventory walk.** Physically trace where CUI lives in your shop, from the moment it arrives until the moment the part ships. Write down every system it touches, every derived artifact it produces, and every person who handles it.

2. **Build an asset inventory that includes the shop floor.** Most small shops have an IT asset list that covers laptops and servers. The CMMC asset inventory has to include CNCs, PLCs, HMIs, CMMs, networked test equipment, and anything else that has an IP address on the shop floor.

3. **Document your scoping rationale in writing with primary-source citations.** Decide your position on derivative files. Write it down. Cite 32 CFR 170.19, the NARA CUI Marking Handbook, the CTI category definition, and your contract language. This document is the centerpiece of your defense plan.

4. **Get your shop floor network segmented.** If your CNCs are on the same flat network as the front office printer, your scope is going to be a nightmare. A properly placed firewall and a VLAN separation is the single highest-leverage technical step you can take.

5. **Document the engineering bridge controls.** Whatever you have on the workstations that push files to the controllers, write it down. Whatever you do not have, build it. This is where most small shops have the largest gap between "what we do" and "what we should do."

6. **Engage the Florida ecosystem.** [FloridaMakes](https://www.floridamakes.com/about/contact-us) has business advisors who can help you find resources. [Cyber Florida at USF](https://cyberflorida.org) has assessment tools and partnerships specifically for small manufacturers in the DIB. The [Manufacturing Extension Partnership](https://www.nist.gov/mep) has a national catalog of cybersecurity programs for small manufacturers. None of this is free, but it is dramatically less expensive than a failed assessment.

7. **Book a C3PAO before everyone else does.** Phase 2 demand is going to massively outstrip C3PAO supply. The shops that booked their assessment in early 2026 are going to be doing business in 2027. The shops that wait until summer 2026 to start scoping are going to be standing in line behind their competitors.

## The bottom line

November 10, 2026 is real. The Specialized Asset rule is not a free pass. The shop floor is in scope. The g-code debate is unresolved, which means the answer a given shop gets depends on which assessor walks through the door.

The shops that will pass their assessments are not the ones that pick the right side of a contested debate. They are the ones that walked in with a documented, defensible scoping position backed by primary sources, compensating controls that hold under either reading, and a data-flow diagram that makes the whole story legible in five minutes.

That is the defense plan. Florida has the manufacturing density, the defense exposure, and the ecosystem support to do this well. The decision in front of every small Florida defense manufacturer right now is whether to be one of the shops that gets it done, or one of the thousands that quietly exit the defense market over the next 24 months.

There is enough time, but only if you start now.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB based in St. Petersburg, Florida, supporting defense, federal, and commercial organizations through CMMC, NIST 800-171, FedRAMP, and HIPAA compliance engagements. Questions about shop floor scoping, OT segmentation, or CMMC readiness can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*
