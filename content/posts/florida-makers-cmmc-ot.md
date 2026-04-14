---
title: "Florida Makers and CMMC: The OT Blind Spot on Your Shop Floor"
date: 2026-04-14
draft: false
tags: ["CMMC 2.0", "OT Security", "Manufacturing", "NIST 800-171", "Defense", "Florida"]
categories: ["Compliance", "Manufacturing"]
summary: "Your CNC machines, PLCs, and IoT sensors are in scope. Most small Florida manufacturers are not thinking about operational technology when they start a CMMC assessment, and it is the gap that kills timelines."
author: "Cameron Hopkin"
---

Most small Florida manufacturers approach CMMC the way they approach IT in general: as an email and file-server problem. They focus on Microsoft 365, on the engineering workstations, on the file shares where part drawings live. They scope a tight enclave around the front-office systems that handle Controlled Unclassified Information, declare victory, and book a C3PAO.

Then their assessor walks onto the shop floor.

What the assessor sees is the part of the business the IT team has been trained to ignore for twenty years. A CNC machine running a g-code program that was generated from a CUI part drawing. A coordinate measuring machine inspecting that part against tolerances pulled from a CUI technical data package. A networked PLC orchestrating the production cell. An HMI on Windows 7 that nobody has touched since 2014 because the vendor's last supported patch was in 2017. A vendor remote access tunnel from the machine OEM that the IT team did not even know existed.

Every one of those devices is now part of the CMMC conversation. The carve-out for "Specialized Assets" that most contractors are leaning on does not mean what they think it means. Phase 2 of the [CMMC rollout begins November 10, 2026](https://blog.waypointca.com/posts/cmmc-level-2-small-business/), and the Florida manufacturers who have been treating operational technology as out-of-scope are about to find out otherwise.

This post is the long version of why, and what to do about it.

## What actually counts as operational technology in a shop

Before getting into the rules, it helps to be precise about what we are even talking about. "OT" is one of those acronyms that sounds technical but covers a much wider footprint than most people realize.

Operational technology is hardware and software that directly monitors or controls the physical environment. In a manufacturing context that includes:

- **CNC machine controllers** running Fanuc, Siemens, Heidenhain, Mazak, Haas, or any of the other dozen control systems on a typical shop floor.
- **Programmable Logic Controllers (PLCs)** from Allen-Bradley/Rockwell, Siemens, Mitsubishi, Omron, and others. CompactLogix and Micro850 devices are particularly common in small manufacturing shops, and they are also currently being [actively targeted by Iranian-affiliated threat actors](https://www.cisa.gov/news-events/cybersecurity-advisories/aa26-097a) using internet-exposed configuration software to reach them.
- **Human Machine Interfaces (HMIs)** running on Windows boxes that often cannot be patched without revalidating the entire production system. Many of these are running operating systems Microsoft stopped supporting years ago.
- **SCADA and historian servers** that aggregate production data and let supervisors see what is happening across the shop.
- **Industrial IoT sensors** measuring temperature, pressure, vibration, machine tool wear, energy consumption, and feeding it back to a manufacturing execution system.
- **Coordinate measuring machines (CMMs)** and other quality inspection equipment that compares finished parts against design specs.
- **Building automation and access control systems** that connect to the same network as everything else.
- **Vendor remote access pathways** that machine OEMs use for diagnostics and software updates.
- **Engineering workstations** running CAM software that translates CAD models into the g-code that gets sent to the CNC.

Note the last item. Engineering workstations are not OT, but they are the bridge between CUI and OT. They are often the first place an assessor will challenge your scope, because they are where the CUI part drawing becomes a CUI machine instruction.

## The Specialized Asset rule that everyone misreads

CMMC defines five asset categories in [32 CFR §170.19(c)(1) Table 3](https://www.ecfr.gov/current/title-32/subtitle-A/chapter-I/subchapter-G/part-170/subpart-D/section-170.19): CUI Assets, Security Protection Assets, Contractor Risk Managed Assets, Specialized Assets, and Out-of-Scope Assets.

Specialized Assets is the category where OT, IIoT, GFE, restricted information systems, and test equipment all live. The official [DoD CMMC Level 2 Scoping Guide](https://dodcio.defense.gov/Portals/0/Documents/CMMC/ScopingGuideL2v2.pdf) describes them as assets that "may or may not process, store, or transmit CUI" but cannot be fully secured to the standard NIST 800-171 controls because of legitimate operational or technical constraints.

Here is what most contractors hear when they read that: "Specialized Assets are out of scope. I do not have to assess my CNC machines."

Here is what the rule actually says: Specialized Assets that process, store, or transmit CUI are **in scope**. They must appear in your asset inventory. They must be documented in your System Security Plan. They must show up on your network and data-flow diagrams. The assessor will verify they are identified, that their function is documented, and that risk-based safeguards are in place. The assessor is not going to walk through all 110 NIST 800-171 controls against a 1998 PLC, but they are going to verify that you have thought about the asset, isolated it, and have a defensible story for how you protect it.

The relief from the full control set is a recognition that you cannot run modern endpoint protection on a Fanuc controller. It is not a recognition that the controller does not exist for compliance purposes. The Peak InfoSec analysts have made this point [forcefully and accurately](https://peakinfosec.com/whitepapers/white-paper-debunking-cmmc-assessment-scope-myths/): treating Specialized Assets as out-of-scope when they actually handle CUI exposes you to the same False Claims Act risk that a misrepresented SPRS score does.

## The trap: how a CNC machine becomes a CUI Specialized Asset

Walk through a normal job in a typical small Florida defense subcontractor.

A prime contractor sends you a contract package. Inside it: a part drawing, a technical data package, a few specifications. The drawing is marked CUI. So is the technical data. The cover sheet has DFARS 252.204-7012 language. Your engineering team uses CAD to model the part, runs the model through CAM software to generate the toolpaths, posts the toolpaths to a g-code program specific to the CNC machine that will cut it. Operator loads the program onto the controller, fixtures the stock, runs the job. CMM inspects the finished part. Shipping documentation is generated. The part goes out the door to the prime.

Now categorize every asset that touched the workflow.

The CAD workstation processes CUI. CUI Asset.

The CAM software runs on a workstation that processes CUI. CUI Asset.

The g-code file generated from the CUI part drawing inherits the CUI marking, because it encodes the same protected information in a different form. [DoDI 5200.48](https://www.esd.whs.mil/Portals/54/Documents/DD/issuances/dodi/520048p.PDF) is clear that CUI status follows the information regardless of format: if the source is CUI, a document derived from it that contains the same controlled information is CUI.

The CNC controller stores and processes that g-code file. The g-code file is CUI. Therefore the CNC controller is a Specialized Asset that processes CUI, which puts it in the CMMC Assessment Scope.

The CMM running the inspection program against CUI tolerances is similarly in scope.

The MES that schedules the job and tracks its progress, if it pulls any CUI metadata from the part traveler, is in scope.

The engineering workstation that posted the g-code to the controller via a network share or a USB stick has a documented data flow path into the CUI Specialized Asset category, which means that flow has to be documented in your network diagram and your SSP.

The vendor remote-access pathway that the machine tool OEM uses to push firmware updates touches the controller. That makes it part of your Security Protection Asset story, and you need to know exactly what authentication, logging, and access control sit on it.

This is not me being aggressive about scope. This is what the rule says. The assessor is going to ask which assets process, store, or transmit CUI. If you say "the engineering workstations" but your CNC controllers are receiving the g-code derived from CUI drawings, your scope statement does not match reality and your assessment is going to fail before it starts.

## Why this is particularly painful for Florida manufacturers

Florida is a top-five state for DoD contract spending. The state's manufacturing sector employs [over 465,000 people across roughly 11,656 companies](https://www.industryselect.com/blog/top-10-manufacturing-companies-in-florida), and the I-4 corridor between Tampa and the Space Coast is one of the densest defense manufacturing clusters in the country. Lockheed Martin in Orlando. L3Harris in Melbourne and Palm Bay. Northrop Grumman in Melbourne. Raytheon's Florida footprint. The Eglin Air Force Base munitions ecosystem in the panhandle. The whole space launch supply chain on the east coast.

Underneath those primes is a long tail of tier-three and tier-four subcontractors. Machine shops with 15 employees making bracket assemblies for missile guidance systems. Specialty platers and finishers. Composite fabricators. Cable harness builders. Electronics assemblers. Most of them are family-owned, most of them are running shop floor equipment that was installed before "cybersecurity" was even a department in any company, and most of them have an IT setup that consists of QuickBooks, an email server somewhere, and a shared drive on a NAS that lives in a closet.

These shops have been getting away with cybersecurity neglect for years because nobody was checking. CMMC is what changes that. The annual senior-officer affirmation in SPRS is a legally significant statement. The C3PAO assessment in Phase 2 is a real audit by a real assessor who will look at real shop floor equipment. The False Claims Act exposure is real, and the DOJ has already collected over $13 million in cybersecurity-related settlements from defense contractors — [$4.6 million from MORSECORP](https://www.justice.gov/opa/pr/defense-contractor-morsecorp-inc-agrees-pay-46-million-settle-cybersecurity-fraud) and [$8.4 million from Raytheon](https://www.justice.gov/opa/pr/raytheon-companies-and-nightwing-group-pay-84m-resolve-false-claims-act-allegations-relating) — before Phase 2 even started.

The state of Florida is not blind to this. [FloridaMakes](https://www.floridamakes.com), the state's official representative of the NIST Manufacturing Extension Partnership, has been working on cybersecurity awareness for the manufacturing sector for years. In August 2024, FloridaMakes [partnered with Cyber Florida at USF](https://cyberflorida.org/floridamakes-partnership-announced/) to expand cybersecurity assessment capabilities specifically for Florida manufacturers and DIB companies. The infrastructure to help Florida manufacturers get this right exists. The bottleneck is awareness and time.

The time bottleneck is real. There are roughly [80 to 100 authorized C3PAOs](https://cyberab.org/Catalog/Certified-Assessors-and-Instructors/Certified-Third-Party-Assessor-Organizations) for an estimated 80,000 organizations needing Level 2 certification. Current capacity is roughly one assessment per C3PAO per month, and many are already booked through the end of 2026. Multiple industry analysts are predicting that 33,000 to 44,000 companies, 15 to 20 percent of the entire defense industrial base, will exit the DoD market between 2025 and 2027 because they cannot complete CMMC compliance in time. The exits will concentrate in exactly the kind of small machine shops Florida is full of. Tier-three subcontractors with $2 million in revenue and $400,000 of defense work cannot easily justify $200,000 of compliance investment under tight margins.

The Florida manufacturers who survive this transition are the ones who started early, scoped honestly, and built shop floor security architectures that match the reality of how parts actually get made.

## The architecture that actually works

The good news is that the technical solution is well understood. The challenge is operational discipline, not invention.

**Step one: find the CUI first.** Before you touch a single piece of equipment, walk the workflow. Where do drawings come in? Email? Customer portal? File sync? Once they arrive, where do they go? Whose workstation? Which file share? Which CAM seat? Which controller? Which inspection program? Which shipping document? Map it on paper. Then map it again to make sure you got it right. Most small shops discover during this exercise that CUI is in three or four places they did not know about, including a personal Dropbox account that an engineer set up in 2019 to share files with a colleague who has since left.

**Step two: segment the shop floor network.** This is the architectural foundation. The OT network has to be a separate broadcast domain from the office network, with a clearly defined boundary, documented connections crossing the boundary, and inspection of any traffic between zones. CISA's guide to [segregating ICS-OT architecture](https://www.cisa.gov/sites/default/files/2023-03/Segregating%20the%20ICS-OT%20Insecure%20by%20Design%20Architecture%20508c%20Rev%20E%20.pdf) walks through the Purdue-style zone model at each level. You do not have to implement Purdue perfectly to get value from it. You do have to know which devices live at which level and what traffic is allowed to cross the boundaries.

For most small shops, this means installing a firewall between the office network and the shop floor network, putting the CNCs and PLCs on their own VLAN with no inbound internet access, and treating any cross-zone traffic (engineering workstation pushing a g-code file, MES collecting machine status) as a controlled and logged data flow.

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

## Six things to do this month

For the small Florida manufacturer reading this and realizing the OT side of CMMC has been a blind spot:

1. **Do a CUI inventory walk.** Physically trace where CUI lives in your shop, from the moment it arrives until the moment the part ships. Write down every system it touches. If you find CUI in a place you did not expect, that is a finding, not a failure.

2. **Build an asset inventory that includes the shop floor.** Most small shops have an IT asset list that covers laptops and servers. The CMMC asset inventory has to include CNCs, PLCs, HMIs, CMMs, networked test equipment, and anything else that has an IP address on the shop floor. Pull the list from your network management tool if you have one. If you do not, walk the shop with a clipboard.

3. **Get your shop floor network segmented.** If your CNCs are on the same flat network as the front office printer, your scope is going to be a nightmare. A properly placed firewall and a VLAN separation is the single highest-leverage technical step you can take.

4. **Document the engineering bridge controls.** Whatever you have on the workstations that push g-code to the controllers, write it down. Whatever you do not have, build it. This is where most small shops have the largest gap between "what we do" and "what we should do."

5. **Engage the Florida ecosystem.** [FloridaMakes](https://www.floridamakes.com/about/contact-us) has business advisors who can help you find resources. [Cyber Florida at USF](https://cyberflorida.org) has assessment tools and partnerships specifically for small manufacturers in the DIB. The [Manufacturing Extension Partnership](https://www.nist.gov/mep) has a national catalog of cybersecurity programs for small manufacturers. None of this is free, but it is dramatically less expensive than a failed assessment.

6. **Book a C3PAO before everyone else does.** Phase 2 demand is going to massively outstrip C3PAO supply. Many C3PAOs are already booked through the end of 2026, with wait times expected to exceed 18 months by Q3. The shops that booked their assessment in early 2026 are going to be doing business in 2027. The shops that wait until summer 2026 to start scoping are going to be standing in line behind their competitors.

## The Florida manufacturer who gets this right

The Florida manufacturer who gets this right looks something like this: A 30-person machine shop in central Florida making precision components for a tier-two prime in the missile defense supply chain. They have eight CNC machines, two CMMs, a small EDM, and a dedicated CMM lab. Annual revenue around $4 million, of which about $1.4 million is DoD work flowing through DFARS 252.204-7012 contracts.

In early 2026 they hire someone (full-time, fractional, or consultant, the title matters less than the function) to own CMMC. That person walks the floor with a notebook for two weeks and produces an asset inventory that matches reality, a CUI flow diagram, and a five-page memo that says "here is what we have, here is what we are missing, here is what it costs to close the gap." The owner reads it, asks hard questions, and signs off on a 12-month plan.

Over the next nine months they segment the network, replace two end-of-life HMI computers, set up a logged jump host for vendor access, deploy a small SIEM that watches the boundary between the shop floor and the office, write the SSP, document the Specialized Assets honestly, run a self-assessment, score it in SPRS at 89 out of 110 with a clean POA&M for three 1-point items, and book a C3PAO for Q3 of 2027. They make the assessment date with three weeks to spare. They pass on the first attempt. They keep their contracts. Their tier-two prime starts giving them more work because the prime trusts their compliance posture.

That is not a hypothetical. It is the playbook. The shops that follow it are going to be fine. The shops that keep treating CMMC as an IT email-server problem are going to find out the hard way that the assessor does not stop at the office door.

The November 10, 2026 deadline is real. The Specialized Asset rule is not a free pass. The shop floor is in scope. Florida has the manufacturing density, the defense exposure, and the ecosystem support to do this well. The decision in front of every small Florida defense manufacturer right now is whether to be one of the shops that gets it done, or one of the 33,000 to 44,000 that quietly exit the defense market over the next 24 months.

The honest answer is that there is enough time, but only if you start now.

---

*Waypoint Compliance Advisory is an SBA-certified SDVOSB based in St. Petersburg, Florida, supporting defense, federal, and commercial organizations through CMMC, NIST 800-171, FedRAMP, and HIPAA compliance engagements. Questions about shop floor scoping, OT segmentation, or CMMC readiness can be directed to [cameron@waypointca.com](mailto:cameron@waypointca.com).*
