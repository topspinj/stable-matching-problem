# Stable Matching Problem

The Stable Matching Problem (SMP) is a classic mathematics problem that involves combinatorial theory of orderded sets. Though SMP was initially described in the context of marriage, it has applications in other fields such as matching medical students to residency programs (e.g., [NRMP](http://www.nrmp.org/matching-algorithm/) and [CaRMS](https://www.carms.ca/the-match/how-it-works/)) and college admissions. 

In the example of marriage, the problem involves a set of women and a set of men of equal size. Both women and men list in order of preference the members of the other sex. For example:

<img src="/imgs/matching.png" width="60%">

The challenge is to assign men to women (or vice versa) in a way that takes into account their preferences. A matching is deemed unstable if:
- woman A and man A are paired but woman A prefers man B **and**
- man B is paired with woman B but prefers woman A 

This would be considered an unstable marriage since woman A and man B simultaneously prefer each other than their respective matches. The goal is to determine the optimal assignments such that all matchings are stable.

<img src="/imgs/unstable-match.png" width="60%">

In 1962, David Gale and Lloyd Shapely developed an [algorithm](http://www.dtic.mil/dtic/tr/fulltext/u2/251958.pdf) to solve this problem. The algorithm works under the following assumptions:
1. Women can only propose to men, not vice versa.
2. If woman $w$ proposes to man $m$ and $m$ is free, then $w$ and $m$ become engaged.
3. If a man gets multiple proposals, he rejects all but his top choice.
4. Each rejected woman proposes to her next best choice regardless of whether that man is currently engaged.
5. If an engaged man receives a proposal from a woman that he prefers over his current woman, he breaks his proposal and becomes engaged to his preferred choice.
6. These steps are repeated until all proposals (matchings) are stable.

Implementation of this algorithm in Python can be found [here](smp.ipynb).
