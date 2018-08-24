# Stable Matching Problem

The Stable Matching Problem (SMP) is a classic mathematics problem that involves combinatorial theory of ordered sets. Though SMP was initially described in the context of marriage, it has applications in other fields such as matching medical students to residency programs and college admissions. The National Resident Matching Program ([NRMP](http://www.nrmp.org/matching-algorithm/)) and the Canadian Resident Matching Service ([CaRMS](https://www.carms.ca/the-match/how-it-works/)) are two examples of residency admission algorithms that aim to optimize SMP.

In the example of marriage, the problem involves two equal sized sets of women and men. Each woman and man is asked to list members of the opposite sex in order of preference. For example:

<img src="/imgs/matching.png" width="80%" style="display:block;margin-right:auto;margin-left:auto;">

The challenge is to pair men and women in a way that takes into account their preferences. A matching is deemed "unstable" if:
- woman A and man A are paired but woman A prefers man B **and**
- man B is paired with woman B but prefers woman A over woman B

This would be considered an unstable marriage since woman A and man B simultaneously prefer each other over their respective matches. The goal is to configure optimal assignments such that all matchings are stable.

<img src="/imgs/unstable-match.png" width="60%" style="display:block;margin-right:auto;margin-left:auto;">

In 1962, David Gale and Lloyd Shapely developed an [algorithm](http://www.dtic.mil/dtic/tr/fulltext/u2/251958.pdf) to solve this problem. The algorithm works under the following assumptions:
- Women and men are binary and heterosexual
- Women can only propose to men, not vice versa.
- If a woman proposes to a man and that man is available, then the woman and man become engaged.
- If a man gets multiple proposals, he rejects all but his top choice.
- A rejected woman proposes to her next best choice regardless of whether that man is currently engaged.
- If an engaged man receives a proposal from a woman that he prefers over his current woman, he breaks his proposal and becomes engaged to his preferred choice.
- These steps are repeated until all proposals ("matchings") are stable.
