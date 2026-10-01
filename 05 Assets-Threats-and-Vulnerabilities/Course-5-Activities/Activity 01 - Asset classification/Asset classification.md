# Asset Inventory Comparison — Activity Summary

## Overview

This activity focuses on comparing a completed asset inventory against a provided exemplar. The goal is to review how network-connected devices are documented and how each asset is classified based on sensitivity.

In cybersecurity, an asset inventory helps identify what exists on a network, who owns it, where it lives, how it connects, and what level of protection it needs. The exemplar is not the only correct answer. It represents one valid way to complete the activity. The important outcome is that the inventory lists common characteristics of network-connected devices and evaluates them according to sensitivity.

---

## Exemplar Orientation

The exemplar tracks devices that have network access. Each row includes:

- Asset name
- Network access
- Owner
- Location
- Notes
- Sensitivity

The exemplar also maps sensitivity levels to access designations:

| Sensitivity | Access designation |
|---|---|
| Restricted | Need-to-know |
| Confidential | Limited to specific users |
| Internal-only | Users on-premises |
| Public | Anyone |

This mapping helps translate an asset’s classification into a practical access rule.

---

## Exemplar Asset Table

| Asset | Network access | Owner | Location | Notes | Sensitivity |
|---|---|---|---|---|---|
| Network router | Continuous | Internet service provider (ISP) | On-premises | Has a 2.4 GHz and 5 GHz connection. All devices on the home network connect to the 5 GHz frequency. | Confidential |
| Desktop | Occasional | Homeowner | On-premises | Contains private information, like photos. | Restricted |
| Guest smartphone | Occasional | Friend | On and off-premises | Connects to the home network. | Internal-only |
| External hard drive | Occasional | Homeowner | On-premises | Contains music and movies. | Confidential |
| Streaming media player | Continuous | Homeowner | On-premises | Payment card information is stored for movie rentals. | Internal-only |
| Portable game console | Occasional | Friend | On and off-premises | Has a camera and microphone. | Internal-only |

---

## Review Criteria

The exemplar follows these guidelines:

- Identify at least three devices on the home network.
- List network access, owner, and location details for each device.
- Include one to two notes about network access or device use.
- Classify each asset based on its level of sensitivity.

The exemplar only includes devices with network access because that matches the scope of the scenario. A broader asset inventory could also include non-network assets, such as a safe, or digital assets, such as family videos.

---

## What Went Well

Comparing the completed inventory to the exemplar shows several strengths:

- **Core details were captured.** The completed inventory identified devices on the home network and recorded network access, owner, and location for each one.
- **Sensitivity ratings were justified.** Classifications were based on the type of data each device holds and who can access it. For example, a desktop with private photos was marked as Restricted, while a streaming media player with payment card information was marked as Internal-only because access was limited to on-premises users.
- **Notes added context.** Including one or two notes per device helped explain why a sensitivity level was chosen.

---

## Where Improvement Is Needed

The comparison also highlights areas for growth:

- **Scope could be wider.** The completed inventory left out several devices that appear in the exemplar, such as the network router, external hard drive, and portable game console. A stronger inventory asks whether each device connects to the network and includes it when the answer is yes.
- **Sensitivity ratings could be more consistent.** Some classifications appeared to be guesses rather than conclusions based on impact. A better approach asks:
  1. What happens if the asset is disclosed, altered, or destroyed?
  2. Who needs access to the asset, and who should be blocked?
- **Classification categories should be used more clearly.** The exemplar uses a clean mapping:
  - Restricted → need-to-know
  - Confidential → limited to specific users
  - Internal-only → users on-premises
  - Public → anyone
- **Owner and location need more attention.** For shared devices, such as a friend’s phone, it matters whether the device is on-premises, off-premises, or both. That detail changes the sensitivity level.

---

## Important Concepts Learned

### 1. Asset inventory

An asset inventory is a record of devices, systems, and data that need protection. It is not just a list. It is a judgment call supported by context.

### 2. Sensitivity classification

Classification depends on impact. If an asset is disclosed, altered, or destroyed, the level of harm helps determine whether it is Restricted, Confidential, Internal-only, or Public.

### 3. Access designation

Access designation turns classification into action. For example:

- Restricted means need-to-know.
- Confidential means limited to specific users.
- Internal-only means users on-premises.
- Public means anyone.

### 4. Network access

Network access can be continuous or occasional. It can also be on-premises, off-premises, or both. These details affect risk and ownership.

---

## Quick Reference

| Requirement | How to approach it |
|---|---|
| See what belongs in the inventory | Ask whether the device connects to the network |
| Record device details | List network access, owner, location, and notes |
| Classify an asset | Evaluate impact if disclosed, altered, or destroyed |
| Map classification to access | Use Restricted, Confidential, Internal-only, or Public |
| Handle shared devices | Check whether location changes the sensitivity level |
| Include non-network assets | Track them when the scenario allows a broader scope |

---

## Activity Takeaway

The main lesson from this activity is that asset inventories become useful when devices are described with enough detail to support classification. Two analysts can look at the same device and choose different sensitivity levels, but the reasoning must match the scenario.

The exemplar represents one possible completion. The completed inventory does not need to match it word for word. What matters is that the inventory identifies network-connected devices, captures their common characteristics, and evaluates them based on sensitivity.
