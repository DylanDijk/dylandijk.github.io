---
title: Projects
icon: fas fa-newspaper
order: 1
---

***

## Tail-robust estimation of factor-adjusted vector autoregressive models for high-dimensional time series

As part of my PhD, alongside my supervisor [Haeran Cho](https://sites.google.com/view/haeran-cho/home), we wrote a paper proposing a methodology to model high-dimensional time-series which can handle heavy-tailed data. The prepint is available [here](https://arxiv.org/pdf/2509.22235), and the corresponding code [here](https://github.com/DylanDijk/truncFVAR).

***

## Created the [CTVsuggest](https://dylandijk.github.io/CTVsuggest/) and [CTVsuggestTrain](https://dylandijk.github.io/CTVsuggestTrain/) R Packages.  
  - The **CTVsuggest** R package outputs suggestions for packages to be added to CRAN Task Views.
  - The **CTVsuggestTrain** R package carries out the model building process.

  These R packages are based on follow up work of my 4<sup>th</sup> year university [dissertation](https://dylandijk.github.io/assets/pdf/Dissertation.pdf).

  The functionality of the CTVsuggest package was announced by [Achim Zeileis](https://www.zeileis.org/) to the CRAN Task View maintainers, on the 22<sup>nd</sup> of March 2023, and was cited in [this report](https://arxiv.org/pdf/2305.17573) describing the transfer of the Task View management to GitHub. Since the release, the package has been frequently used by maintainers, with examples given below.
   <details>

  <summary markdown="span" style="color:#4863A0">Feedback from Task View Maintainers</summary>
<div markdown="1">

Feedback just after the release in 22/03/23:

  **Michael Dewey**, maintainer of the [MetaAnalysis](https://github.com/cran-task-views/MetaAnalysis) Task View, wrote:

  > "Just for your info of the top twenty for MetaAnalysis five 
  were definitely relevant and all occurred in the top ten. 
  At least three of these have been in the CTV at some point 
  but fallen off CRAN and then come back. It also found two 
  more which I think are of peripheral relevance. I will 
  have a think about them."

  These two commits were made: [Commit 1](https://github.com/cran-task-views/MetaAnalysis/commit/f088a31930fee9df30979ad89a372a9e187d1ad7) and [Commit 2](https://github.com/cran-task-views/MetaAnalysis/commit/223e53f521ed7af137de5a745f9a9dfcab1e565a) afte the package announcement.

  

  **Bill Denney**, maintainer of the [Pharmacokinetics](https://github.com/cran-task-views/Pharmacokinetics) Task View, wrote:

  > "Thanks for the package.  I just updated the Pharmacokinetics CTV using it,
and it provided a list of several more packages that I was not aware of."

A [commit](https://github.com/cran-task-views/Pharmacokinetics/commit/f841bfaa399e211edca71fdffee973b3ff5c5acc) was made.

  ***
  Further examples of CTVsuggest being used for Task View maintenance:
  - 26/03/2023 - [**Commit**](https://github.com/cran-task-views/ChemPhys/commit/05f4fe0d35f0e01ad11ebfe793fd8174dccb376f) titled: "many adds, including many from CTVsuggest" was made in the *ChemPhys* Task View.
  - 12/04/2023 - In the *Distributions* Task View, CTVsuggest has been [**added to the workflow**](https://github.com/cran-task-views/Distributions/commit/6439439cc76eee9d59065824c2607e8efb6c111c).
  - 13/04/2023 - Commits made in *MissingData* Task View: [**1**](https://github.com/cran-task-views/MissingData/commit/aa7f5b98069babaaceea4dc0a12642da2440011c), [**2**](https://github.com/cran-task-views/MissingData/commit/ec67663a91bae4a3d1afb8a8a38363ebee3b0144), [**3**](https://github.com/cran-task-views/MissingData/commit/66bc1e0a2ca65a42e5f677862e2eefa4bef7fc33).
   - 09/05/2023 - [**Issue**](https://github.com/cran-task-views/Hydrology/issues/141#issue-1702686855) in the *Hydrology* Task View agreeing with CTVsuggest suggestions.
  - 27/10/2023 - [**Issue**](https://github.com/cran-task-views/Omics/issues/14) opened in *Omics* Task View.
  - 27/03/2024 - Additions in the *Epidemiology* Task View, with commits mentioned in [**this issue**](https://github.com/cran-task-views/Epidemiology/issues/29#ref-commit-c85ef37).
  - 20/09/2024 - Additions in the *SportsAnalytics* Task View, with commits mentioned in [**this issue**](https://github.com/cran-task-views/SportsAnalytics/issues/13).
  - 19/11/2024 - [**Issue**](https://github.com/cran-task-views/DynamicVisualizations/issues/13#issue-2673539303) in the *DynamicVisualizations* Task View.
  - 09/12/2024 - [**Issue**](https://github.com/cran-task-views/Phylogenetics/issues/9) in the *Phylogenetics* Task View, where they added a bunch of recommended packages.
  - 09/12/2024 - [**Issue**](https://github.com/cran-task-views/Paleontology/issues/6) in the *Paleontology* Task View, looking at suggestions from CTVsuggest.
  - 05/12/2025 -  [**Commit**](https://github.com/cran-task-views/NetworkAnalysis/commit/0fb8a5702bd1d259d051b2980540c8f212086790) titled: "Suggestions from CTVsuggest" was made in the *NetworkAnalysis* Task View.
  - 19/12/2025 -  [**Commit**](https://github.com/cran-task-views/TeachingStatistics/commit/25482090ee1d2cd1aa8668780b79e20334eeecf5) titled: "Update TeachingStatistics.md using the CTVsuggest package" was made in the *TeachingStatistics* Task View.

</div>
</details>