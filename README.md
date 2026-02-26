### Inferential Statistics (The "What-if" - using probability to predict what could happen)

---

# 🎲 Predictable Playlists: Probability Modeling for Track Selection
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Statistics](https://img.shields.io/badge/Applied%20Statistics-0078D4?style=for-the-badge&logo=analytics&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)

### *Bridging Descriptive and Inferential Statistics*
**Probability Theory** | **Binomial Distributions** | **Strategic Forecasting**

---

## 📌 Project Overview
As a follow-up to my [Spotify Hit Analysis](https://github.com/ayushi-gajendra/Spotify-hit-analysis), this project moves from summarizing historical data to **predicting future outcomes**. By identifying the underlying probability distributions of track features, I modeled the likelihood of specific musical "modes" appearing in a curated set of songs.

## 📂 The Business Problem
A curator needs to understand the risk of a playlist's mood. If a "Major" modality represents a positive/bright sound, how likely is it that a random selection of 10 tracks will result in a completely "Minor" (darker) set? This project uses math to answer that question before the first song is even played.

---

## 📌 From "What Is" to "What If"
My previous project focused on **Descriptive Statistics** (summarizing historical data). This project represents a transition into **Inferential Statistics**, where I use probability theory to predict future outcomes and assess operational risks in playlist curation.

---

## ⚙️ Analytical Methodology

### 1. The Bernoulli Foundation (The Single Event)
I analyzed the `mode` feature (Major = 1, Minor = 0). Since this is a binary outcome, it follows a **Bernoulli Distribution**.
* **Finding the Probability ($p$):** By calculating the average frequency in the dataset, I established that a single track has a **58.73%** chance ($p = 0.5873$) of being in a Major key.

<p align="center">
  <img src="mode distribution.png" width="60%" />
</p>

### 2. Scaling to a Set (The Binomial Model)
To simulate a real-world scenario, I modeled a group of **10 independent tracks** ($n = 10$). This transition from a single event to a group of events follows a **Binomial Distribution**.

### 3. Mapping Outcomes (PMF vs. CDF)
* **Probability Mass Function (PMF):** Used to calculate the exact likelihood of having exactly $X$ major tracks.
* **Cumulative Distribution Function (CDF):** Used to calculate the risk of "at most" a certain number of tracks.

---

## 📊 Statistical Findings

### Probability & Cumulative Distribution Table (Sample of 10 Tracks)
| # Major Tracks | Probability (PMF) | Cumulative Prob (CDF) | Strategic Interpretation |
| :--- | :--- | :--- | :--- |
| **0** | 0.00014 | 0.00014 | 0.01% chance of an all-minor playlist. |
| **1** | 0.00204 | 0.00218 | Negligible probability for highly skewed sets. |
| **2** | 0.01306 | 0.01524 | Risk of a 20% major playlist is only ~1.5%. |
| **3** | 0.04955 | 0.06479 | Baseline for "diverse" mood sets. |
| **4** | 0.12341 | 0.18820 | ~40% chance of having 5 or fewer major tracks. |
| **5** | 0.21078 | 0.39897 | Near equal split of mood is a 21% occurrence. |
| **6** | **0.24999** | **0.64896** | **Most Likely Outcome:** 1 in 4 sets will have 6 major tracks.  |
| **7** | 0.20332 | 0.85228 | 85% probability of having at most 7 major tracks. |
| **8** | 0.10851 | 0.96079 | Highly favorable toward major modality. |
| **9** | 0.03432 | 0.99512 | Extreme major skew (90%) is a ~3% chance. |
| **10** | 0.00488 | 1.00000 | 0.4% chance of a perfectly uniform major playlist. |



<p align="center">
  <img src="PMF for Number of Major tracks in a List of 10.png" width="45%" />
  <img src="CDF for Number of Major Tracks in a List of 10.png" width="45%" />
</p>

---

### 🔍 Key Insights:
* **The Expected Value:** With $p=0.5873$ and $n=10$, the "expected" number of major tracks is ~6. This aligns with the PMF peak at $X=6$.
* **Risk Mitigation:** The CDF shows that it is extremely rare (0.01%) to accidentally generate an all-minor playlist. This provides a high level of confidence for curators seeking "bright" musical sets.

---

## 🛠️ Formulas & Logic
* **Mean as Probability:** I calculated the average of the binary `mode` column to define my $p$ value.
* **Binomial Calculation:** Used to determine how successes (Major tracks) are distributed across a fixed number of trials (10 songs).
* **PMF Logic:** $P(X=k)$ — The "weight" of a specific outcome.
* **CDF Logic:** $P(X \le k)$ — The "running total" of all probabilities up to that point.

---

## ⚙️ The Strategic Logic Chain (Methodology)

To build this predictive model, I followed a structured 5-step statistical lifecycle:

### 1. Defining the Single Event (Bernoulli Distribution)
In data science, we first analyze the nature of a single data point. Since a song modality can only be Major (1) or Minor (0), this is a **binary outcome**.
* **The Theory:** This is a **Bernoulli Distribution**—the simplest building block of probability.
* **The Strategic "Why":** We must establish the "Success Rate" ($p$) for one song before we can predict the behavior of a group. 

### 2. Turning Data into a "Rule" (The Law of Large Numbers)
I calculated the **Average Frequency** of Major songs across 3,000 tracks.
* **The Action:** The dataset revealed a mean of **0.5873**.
* **The Thought Process:** According to the **Law of Large Numbers**, as our sample size grows, the average frequency becomes our "True North."
* **The Strategic "Why":** This average transforms raw history into a functional tool ($p = 0.5873$), serving as the "Law of the Dataset" for all future predictions.

### 3. Scaling to a Group (Binomial Distribution)
A DJ doesn't play one song; they play a set. When you combine multiple Bernoulli trials (e.g., a 10-song playlist) and count the successes, the distribution shifts.
* **The Theory:** This is a **Binomial Distribution**.
* **The Strategic "Why":** It allows for real-world risk assessment. If 58% of songs are Major, what are the odds of a 10-song playlist being entirely Minor (0.01%)? 

### 4. Mapping Points of Success (PMF)
I examined the **Probability Mass Function (PMF)** for outcomes 0 through 10.
* **The Logic:** Probability "sits" on whole numbers because you cannot have 4.5 songs (Discrete Data).
* **The Strategic "Why":** The PMF identifies the **Most Likely Scenario**. With an **Expected Value ($E[X]$)** of $10 \times 0.5873 = 5.87$, the model correctly peaks at 6 songs, telling the curator what is "normal."

### 5. Analyzing Risk Accumulation (CDF)
Finally, I calculated the **Cumulative Distribution Function (CDF)**.
* **The Logic:** In operations, we rarely ask "What is the chance of exactly 4?" We ask "What is the chance of **at most** 4?" 
* **The Strategic "Why":** The CDF is a "Running Total" of probability. It showed that there is a **~40% chance** of having 5 or fewer Major tracks, helping a curator manage the emotional "weight" of a set.

---

## 🔍 PMF vs. PDF: Why PMF?
It is critical to distinguish between these two for data integrity:
* **PMF (Probability Mass Function):** Used here because our data is **Discrete** (countable songs).
* **PDF (Probability Density Function):** Used for **Continuous** data (like Energy or Valence scores).
* **Conclusion:** You cannot use a PDF for song counts because 2.33 songs do not exist in a playlist.

---

## 💡 Strategic Takeaways
* **Predictability:** The high $p$ value (0.58) makes it statistically difficult to accidentally create an "all-minor" set.
* **Operational Baseline:** By calculating the average first, we established a baseline that allows us to flag any playlist with fewer than 3 major songs as a "mathematical outlier."

---

## 🎓 Project Credits
This analysis was developed as part of the **Applied Statistics for Data Analytics** course by **DeepLearning.AI** on Coursera. It focuses on using discrete distributions to solve predictive problems in media and entertainment.

---

## 👤 About the Author
**Ayushi Gajendra** *Product & Operations Analyst | Ex-EdTech Co-founder*
* I specialize in using **Inferential Statistics** to reduce business uncertainty and drive data-backed strategy.
