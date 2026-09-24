# LLM Survey Framework

> A short reading note on [NBER Working Paper 34308](https://www.nber.org/papers/w34308).

![The blue NBER logo](https://upload.wikimedia.org/wikipedia/en/thumb/4/4e/National_Bureau_of_Economic_Research_logo.svg/1280px-National_Bureau_of_Economic_Research_logo.svg.png)

## Paper at a glance

**Title:** *LLM Survey Framework: Coverage, Reasoning, Dynamics, Identification*  
**Authors:** Jing Cynthia Wu, Jin Xi, and Shihan Xie  
**Paper number:** `w34308`

**Publication:** October 2025  
**JEL codes:** `C83` (survey methods), `E31` (inflation), and `E52` (monetary policy)

The authors propose a framework for using large language models (LLMs) in surveys. Their approach aims to combine the scale of computational methods with the interpretability of human research designs. In a study of inflation expectations, the framework recovers human-comparable treatment effects at roughly **1/1,000 of the cost**. The result is ~~a replacement for human surveys~~ a complement to them.

The central problem is that human surveys are expensive, cannot usually be run retrospectively, and often record an answer without the respondent's reasoning. The proposed framework uses LLM agents as synthetic survey respondents while trying to preserve the structure of a real randomized experiment.

## Main contributions

1. **Retrospective coverage:** extend a benchmark survey beyond its original period.
2. **Economic reasoning:** study how agents form expectations.
3. **Dynamic effects:** trace how treatment effects change over time.
4. **Clean identification:** preserve a randomized-control-trial perspective.

The paper also expands a ten-wave human survey from 2018--2023 to more than **50 waves** reaching back to 1990.

## How the framework works

The design rests on two methodological foundations:

1. **Date restriction:** each agent is instructed to answer as if it were living at the survey date and to ignore later events. This is intended to reduce hindsight bias. The authors test the instruction with events such as 9/11, the Iraq invasion, the Lehman Brothers bankruptcy, presidential elections, and the COVID-19 pandemic. Awareness is generally near zero before an event and close to universal afterward.
2. **Internal consistency:** the same personas can be reused across treatment arms and survey waves. This creates balanced synthetic panels, makes follow-up observations possible, and keeps treatment wording comparable over time.

In the main validation exercise, the authors draw **200 personas** from the New York Fed's Survey of Consumer Expectations. Each persona includes characteristics such as age, gender, marital status, education, income category, and U.S. state. The implementation uses GPT-4.1, with GPT-5 used as a robustness check.

### Survey flow

| Stage | What happens |
| --- | --- |
| Persona | Define a synthetic respondent with fixed demographic attributes. |
| Knowledge restriction | Limit the respondent to information available at the survey date. |
| Prior | Elicit a probabilistic 12-month inflation forecast. |
| Treatment | Randomly provide no information or one of three factual signals. |
| Posterior | Ask for a new numerical inflation forecast and written reasoning. |

The three treatment arms are:

- **T1:** information about past U.S. inflation.
- **T2:** the Federal Reserve's 2% inflation target.
- **T3:** the Federal Open Market Committee's inflation forecast.

### Channels examined

- Mean reversion
- Individual attention
- Information and expectation formation

The reasoning responses are classified into five categories within three broader channels:

| Economic channel | Reasoning categories | Main interpretation |
| --- | --- | --- |
| Mean reversion | Normal; normalizing | Whether inflation is expected to remain near, or return toward, its usual level |
| Attention | Personal observation; monetary policy | Whether agents focus on household prices or central-bank information |
| Business cycle | Business-cycle conditions | Whether expansion, recession, or recovery shapes expectations |

During the high-inflation example (2022Q4), **68%** of responses describe inflation as normalizing toward its usual level, compared with **10%** in the low-inflation example (2018Q2). Personal price observations appear in **54%** of high-inflation responses versus **30%** of low-inflation responses. References to monetary policy are rare in both periods.

## Evidence and results

The validation exercise replicates the multi-wave human experiment of Weber et al. (2025). The main pattern is state-dependent updating: informational treatments have stronger effects when inflation is low and weaker effects when inflation is high.

| Correlation between treatment effect and inflation | T1: Past inflation | T2: Fed target | T3: Fed forecast | Pooled |
| --- | ---: | ---: | ---: | ---: |
| LLM survey | 0.92 | 0.73 | 0.85 | 0.79 |
| Human benchmark | 0.69 | 0.87 | 0.13 | 0.57 |

The authors then extend the past-inflation treatment back to 1990 and run more than 50 waves. The extended results remain consistent with the main pattern, although the relationships are weaker for some treatments. The reported correlations with inflation are **0.61 for T1**, **0.18 for T2**, and **0.76 for T3**.

### Dynamic effects

The same agents are followed monthly for up to one year after the initial treatment. Treatment effects are approximately **half as large after three months**, become statistically insignificant after six months, and disappear within about twelve months. This frequency would be difficult and costly to achieve with repeated human interviews.

### Clean identification

The authors also give agents a factual inflation number that had not yet been publicly released at the survey date. Because the information is excluded from the prior knowledge set, any change in expectations can be more cleanly attributed to the treatment. The clean and non-clean treatment-effect series have a correlation of **0.54**, showing that identification choices can matter even when the broad economic conclusion remains unchanged.

## Comparison

| Feature | Traditional human survey | LLM-based survey |
| --- | --- | --- |
| Historical reach | Limited waves | 50+ waves in the example |
| Marginal cost | Relatively high | About 1/1,000 as high in the study |
| Experimental design | Possible | Designed to preserve clean identification |
| Main challenge | Recruitment and repetition | Validating human comparability |

## My takeaway

> LLM surveys may make research designs possible that would be too expensive or too slow with repeated human surveys.

That promise should still be tested carefully. A model can reproduce an average treatment effect without reproducing every human mechanism. **Validation, transparency, and careful identification remain essential.**

## Limitations and open questions

- LLM responses are not human responses, even when their aggregate patterns look similar.
- Synthetic data can understate genuine variation across people.
- Results may depend on the model, prompt wording, persona construction, and knowledge cutoff.
- The reasoning categories are produced through a human--LLM coding process, so classification still involves judgment.
- The paper focuses on U.S. inflation expectations; applications to housing, labor markets, or other countries require new validation.

## A small research checklist

- [x] Identify the treatment and outcome.
- [x] Compare the LLM results with human-survey evidence.
- [ ] Test whether the result generalizes to another topic.
- [ ] Report sensitivity to prompts and model versions.

## Method sketch

```text
benchmark human survey
	|
	v
randomized treatment -> LLM respondents -> estimated effect
	|                                      |
	+------------ compare and validate ---+
```

The central question can be written informally as:

$$\text{credible LLM survey} = \text{scale} + \text{reasoning} + \text{identification}$$

<details>
<summary>Source details</summary>

This note summarizes the attached 61-page working paper, especially Sections 2--7 and the main validation tables. It is not a substitute for reading the full paper.

</details>

---

*Source:* [NBER, Working Paper 34308](https://www.nber.org/papers/w34308)[^1]  
*Last checked:* 2026-09-24

[^1]: The paper is a working paper, so its findings may develop in later versions.

<!-- Markdown practice: headings, emphasis, links, image, lists, task list, table, code, quote, math, HTML, and a horizontal rule. -->