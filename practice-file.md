# LLM Survey Framework

> A short reading note on [NBER Working Paper 34308](https://www.nber.org/papers/w34308).

![The NBER logo](https://www.nber.org/themes/custom/nber/logo.svg)

## Paper at a glance

**Title:** *LLM Survey Framework: Coverage, Reasoning, Dynamics, Identification*  
**Authors:** Jing Cynthia Wu, Jin Xi, and Shihan Xie  
**Paper number:** `w34308`

The authors propose a framework for using large language models (LLMs) in surveys. Their approach aims to combine the scale of computational methods with the interpretability of human research designs. In a study of inflation expectations, the framework recovers human-comparable treatment effects at roughly **1/1,000 of the cost**. The result is ~~a replacement for human surveys~~ a complement to them.

## Main contributions

1. **Retrospective coverage:** extend a benchmark survey beyond its original period.
2. **Economic reasoning:** study how agents form expectations.
3. **Dynamic effects:** trace how treatment effects change over time.
4. **Clean identification:** preserve a randomized-control-trial perspective.

The paper also expands a ten-wave human survey from 2018--2023 to more than **50 waves** reaching back to 1990.

### Channels examined

- Mean reversion
- Individual attention
- Information and expectation formation

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

This note summarizes the NBER abstract and metadata. It is not a substitute for reading the full working paper.

</details>

---

*Source:* [NBER, Working Paper 34308](https://www.nber.org/papers/w34308)[^1]  
*Last checked:* 2026-09-24

[^1]: The paper is a working paper, so its findings may develop in later versions.

<!-- Markdown practice: headings, emphasis, links, image, lists, task list, table, code, quote, math, HTML, and a horizontal rule. -->