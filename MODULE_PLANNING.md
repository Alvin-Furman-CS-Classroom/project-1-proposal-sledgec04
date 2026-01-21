# Module Planning: Music Recommendation System

## System Theme
A music recommendation system that takes Spotify data and finds similar songs, using features like artist, tempo, genre, featured artists, writers, and producers. The system learns from your playlists and can find unpopular music that matches your preferences. The goal is for this to be as broad as possible. Spotify's custom playlists are good, but after some time, they begin repeating the same known songs. I want the selection to be more curated, as if a DJ was putting together a setlist while keeping the above features in mind.

## Proposed Module Order & Topics

### Module 1: Feature Extraction, Processing, and Knoweldge Base Representation
**Topic:** Data processing and knowledge base representation

**Purpose:** Extract and process features from Spotify data (tempo, genre, artist, featured artists, writers, producers, language) and create a structured knowledge base for the later modules.

**Input:**  A set of Spotify songs with their metadata

**Output:**  A knowledge base of facts and relations

**Integreation:**  This provides a preliminary level of data processing to create a knowledge base that can be used in the rest of the modules.

**Prerequisites:** Knowledge Representation basics and propositional logic


---

### Module 2: Machine Learning
**Topic:** Machine Learning

**Purpose:** Learn preferences from your playlists to identify patterns in:
- Tempo preferences
- Artist connections
- Genre connections
- Other feature preferences

**Input:** The knowledge base from module 1

**Output:** Learned weights for combining features

**Prerequisites:** Machine Learning and Supervised Learning including model optimization

---

### Module 3: Preference Combination (Choose one topic)
**Topic:** Classification

**Purpose:** Classify songs as "candidate" vs "non-candidate" based on learned + user preferences, filtering the database before search

**Input:** The Knowledge base from module 1 and Module 2's weights

**Output:** Weights made into features

**Prerequisites:** Supervised learning, Knowledge Base from Module 1, Model from Module 2

---

### Module 4: Search
**Topic:** Search (Uniform Cost, A*, Beam Search, etc.)

**Purpose:** Search for similar songs in the database using:
- Learned weights from Module 2
- User-specified preferences from Module 3
- Explicitly avoids popularity bias

**Key Feature:** Search treats all songs equally, ensuring unpopular music can be found

**Input:** Candidate songs from Module 3, knowledge base features

**Output:** Ranking of top k songs with scores

**Prerequisites:** State-space modeling, successors, path cost, graph search algorithms, Module 1 2 and 3

---

### Module 5: Clustering
**Topic:** Clustering

**Purpose:** Organize search results into diverse groups/clusters to:
- Provide variety in recommendations
- Group similar results together
- Ensure recommendations span different styles

**Input:** Ranked candidates from module 4

**Output:** Clustered groups of candidates

**Prerequisites:** Clustering, Previous modules

---

## Feasibility Study

_A timeline showing that each module's prerequisites align with the course schedule. Verify that you are not planning to implement content before it is taught._

| Module | Required Topic(s) | Checkpoint Due |
| ------ | ---------------- | -------------- |
| 1      | KR + Logic       | _1/29_         |
| 2      | ML (Supervised)  | _2/5___        |
| 3      | Classification   | _2/12___       |
| 4      | Search (UCS/A*)  | _2/19___       |
| 5      | Clustering       | _2/26___       |

**Legend (what each “Required Topic(s)” means):**
- **KR + Logic**: knowledge representation (facts/relations); propositional logic basics (only if you include rule queries/inference)
- **ML (Supervised)**: feature/label setup from playlists; training/optimization; basic evaluation
- **Classification**: candidate vs non-candidate classifier; thresholding; precision/recall-focused evaluation
- **Search (UCS/A*)**: state-space formulation; path cost; UCS/A*/Beam (whatever you pick); heuristic design (if A*); complexity tradeoffs
- **Clustering**: k-means/hierarchical/etc. (as covered); distance metrics; feature scaling/normalization; cluster evaluation

## Coverage Rationale

_Brief justification for your choice of topics. Why do these topics fit your theme? What trade-offs did you consider?_
Originally, I wanted to do a search that gave weight to specific features. This might be too difficult given the scope of the class. I also wanted to include very unpopular songs in the searches to find songs that I might like but never find on my own, while the consideration is still there, I am concerned about the feasibility. The theme of this project lies heavily in machine learning, so most of my modules deal with that directly while including knowledge bases to help with that.