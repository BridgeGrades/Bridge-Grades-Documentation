# **Bridge Grades Data Sources**

```{admonition} Overview
:class: tip

Bridge Grades relies on **10 primary data sources** to evaluate congressional collaboration and bipartisanship. Each source measures different aspects of legislative behavior, from bill sponsorship to public communication patterns. This document provides detailed information about each source, how to acquire the data, and how it contributes to the final Bridge Grade calculation.
```

## **Primary Data Sources**

### **1. Plural Policy Bill Sponsorship Data - Sources A & B**

**Organization:** [Plural Policy](https://open.pluralpolicy.com/)

**Description:** Comprehensive bill sponsorship and cosponsorship data for the U.S. Congress, tracking legislative collaboration patterns.

**Data Acquisition:**
- **Website:** https://open.pluralpolicy.com/data/session-csv/
- **Access:** Free download of session-specific CSV files
- **Format:** CSV files with bill sponsorship records
- **Coverage:** Complete bill sponsorship data for current and historical Congresses

**Bridge Grades Metrics:**
- **Source A:** Authors of Bills with Cross Party Sponsors - Count of sponsored bills with bipartisan cosponsorship
- **Source B:** Ranked People who Cosponsor Bills - Count of bills cosponsored from the opposite party

**Current Weight:** 3.0 (A), 2.0 (B)

---

### **2. Americas Political Pulse (APP) - Sources C, D, E, F**

**Organization:** [Polarization Research Lab](https://americaspoliticalpulse.com/)

**Description:** The Polarization Research Lab captures comprehensive data on politicians' public communications, measuring them across multiple categories including Policy Discussion, Constructive Debate, Personal Attacks, Accomplishments, and Bipartisanship/Compromise.

**About the Organization:** "A research group and resource hub dedicated to applying science to the study of polarization and democracy. Founded on more than a decade of research by top scholars in the field at Dartmouth College, Stanford University, and the University of Pennsylvania, PRL advances the study of partisan animosity by collecting data, testing new ideas through rigorous science, and sharing the data and findings with others."

**Data Acquisition:**
- **Website:** https://americaspoliticalpulse.com/data/
- **Access:** Select "US officials" in left menu, then "Download 2025"
- **Format:** CSV files with communication data
- **Coverage:** All forms of public communication including floor speeches, newsletters, press releases, and social media posts

**Bridge Grades Metrics:**
- **Source C:** Bipartisan Communication Sum - Total count of bipartisan communications per legislator
- **Source D:** Bipartisan Communication Percentage - Share of total communications that are bipartisan
- **Source E:** Personal Attack Sum - Total count of personal attacks per legislator
- **Source F:** Personal Attack Percentage - Share of total communications that are personal attacks

**Current Weight:** 1.0 each (C, D, E, F)

---

### **3. Cook Political Partisan Voting Index (PVI) - Source M**

**Organization:** [Cook Political Report](https://www.cookpolitical.com/)

**Description:** Measures how partisan each congressional district and state is relative to the national average. This data rewards bridging behaviors by politicians who represent highly partisan districts as a "degree of difficulty" adjustment.

**About the Metric:** "We reward bridging behaviors by those who represent highly partisan voting districts as a 'degree of difficulty.' This rewards bridging bravery by politicians who could otherwise resort to divider behaviors and still win re-election."

**Data Acquisition:**
- **Website:** https://www.cookpolitical.com/cook-pvi
- **Access:** Paid subscription required
- **Format:** Excel files with district and state-level PVI data
- **Coverage:** All 435 House districts and 50 states for Senate races

**Bridge Grades Metrics:**
- **Source M:** Cook Political PVI - District/state partisan lean used as multiplier for degree of difficulty

---

### **4. VoteView Ideological Scores - Source N**

**Organization:** [VoteView](https://voteview.com/)

**Description:** Provides ideological positioning of members of Congress based on roll-call voting patterns. VoteView allows users to view every congressional roll call vote in American history on a map of the United States and on a liberal-conservative ideological map.

**About the Data:** "Voteview.com allows users to view every congressional roll call vote in American history on a map of the United States and on a liberal-conservative ideological map including information about the ideological positions of voting Senators and Representatives."

**Data Acquisition:**
- **Website:** https://voteview.com/data
- **Access:** Free download
- **Format:** CSV files with member ideology data
- **Coverage:** All members of Congress with ideology scores based on voting patterns

**Bridge Grades Metrics:**
- **Source N:** VoteView Member Ideology Scores - Absolute distance from ideological center used as multiplier

---

### **5. Lugar Bipartisan Index (Conceptual Foundation)**

**Organization:** [Lugar Center](https://www.thelugarcenter.org/)

**Description:** A weighted index that measures bipartisan bill authoring and sponsorship patterns. While not directly used in Bridge Grades calculations, this index provides the conceptual foundation for our bill sponsorship metrics.

**About the Index:** "A consistently low score on this index will be a very strong indication that a legislator is viewing his or her duties through a partisan lens. Conversely, a consistently high score is a strong indication that a legislator is prioritizing problem solving and open to working with the other party when possible."

**Relationship to Bridge Grades:** Our Sources A and B (bill sponsorship metrics) are inspired by and aligned with the Lugar Bipartisan Index methodology.

---

### **6. GovTrack Report Cards (Conceptual Foundation)**

**Organization:** [GovTrack](https://www.govtrack.us/)

**Description:** Provides rankings on legislator performance in authoring and co-sponsoring bipartisan legislation. Specifically includes two measures: (1) authoring bills that attract co-sponsors from another party, and (2) co-sponsoring bills authored by a member from another party.

**Relationship to Bridge Grades:** Our Sources A and B directly implement these two GovTrack measures using Plural Policy data.

---

## **Base Data Collection Sources**

### **Congress.gov API - Master Legislator Roster**

**Organization:** [Congress.gov](https://www.congress.gov/)

**Description:** Official congressional member data providing the master roster of current legislators with unique bioguide_id identifiers.

**Data Acquisition:**
- **API:** https://api.congress.gov/v3/member/congress/119/
- **Access:** Free with API key registration
- **Format:** JSON API responses
- **Coverage:** All current House Representatives and Senators

**Bridge Grades Role:** Provides the foundational legislator dataset (`119th_Congress_20250809.csv`) that serves as the master roster for all subsequent data processing and analysis.

---

### **OpenStates People Repository - Legislator Biographical Data**

**Organization:** [OpenStates](https://openstates.org/)

**Description:** Comprehensive legislator biographical database with multiple identifier schemes including bioguide_id mappings.

**Data Acquisition:**
- **Repository:** https://github.com/openstates/people.git
- **Access:** Free, open source
- **Format:** YAML files per legislator
- **Coverage:** Historical and current legislators with comprehensive biographical data

**Bridge Grades Role:** Enables accurate legislator identification when processing bill sponsorship data from Plural Policy sources by providing bioguide_id mappings.

---

## Data Source Summary Table

| Source | Organization | Data Type | Access | Current Weight | Bridge Grades Metric |
|--------|--------------|-----------|---------|----------------|---------------------|
| **A** | Plural Policy | Bill Sponsorship | Free | 3.0 | Authors of bills with cross-party sponsors |
| **B** | Plural Policy | Bill Cosponsorship | Free | 2.0 | Cosponsors of cross-party bills |
| **C** | Americas Political Pulse | Communication | Free | 1.0 | Bipartisan communication sum |
| **D** | Americas Political Pulse | Communication | Free | 1.0 | Bipartisan communication percentage |
| **E** | Americas Political Pulse | Communication | Free | 1.0 | Personal attack sum |
| **F** | Americas Political Pulse | Communication | Free | 1.0 | Personal attack percentage |
| **M** | Cook Political | PVI Data | Paid | Bonus | District partisan lean multiplier |
| **N** | VoteView | Ideology Scores | Free | Bonus | Ideological distance multiplier |
| **P** | Manual | Caucus Membership | Manual | Bonus | Problem Solvers Caucus bonus |
