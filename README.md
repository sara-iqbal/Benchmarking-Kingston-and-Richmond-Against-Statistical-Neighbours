# How do Kingston and Richmond compare?

**Benchmarking two London boroughs' children's services against their statistical neighbours, London and England, using DfE open data.**

https://colab.research.google.com/drive/1XSA86KTGX980aSieZBPievBDei_ZiY5M

## The problem

Performance figures mean very little in isolation. If a council completes 80% of its assessments within 45 working days, is that good? It depends entirely on what you compare it with.

Children's services teams answer that question with benchmarking. The Department for Education publishes a list of **statistical neighbours** for every council in England: the ten councils most similar to it on things like deprivation, housing and population. Comparing a council with its neighbours is fairer than comparing it with England as a whole, because like is being compared with like.

I wanted to answer a practical question a performance team would actually be asked: **where do Kingston and Richmond stand, compared with councils like them, and where should a manager look first?**

## How I approached it

Everything runs in one Google Colab notebook.

**1. Load the official data.** I used the DfE's *Children in Need* and *Children Looked After* releases for the year ending 31 March 2025, plus the DfE's statistical neighbour benchmarking tool. Release files change their names from year to year, so the notebook recognises each data set by its **columns** rather than its file name. That makes it reusable when next year's data comes out.

**2. Build twelve indicators for every council in England.** These run from referrals through assessments, child protection and children in care, to care leavers. Where the DfE publishes counts, I recalculated percentages from the counts; for rates, I used the same population estimates the DfE uses. I treated suppressed values (marked `c`, `x`, `z` and so on) as missing, never as zero.

**3. Check the definitions.** Before comparing anything, I checked that my England figures matched the headline figures the DfE publishes. If those don't match, nothing built on them can be trusted.

**4. Benchmark.** For Kingston and Richmond I compared each indicator with the average of their ten statistical neighbours (a simple mean, as in the DfE's LAIT tool), with London and with England. I also ranked each borough among all 155 councils. Each comparison gets a plain verdict: better, worse or in line, or for context measures, simply higher or lower.

**5. Explain it.** The notebook writes an insight brief for a non-technical manager and exports tidy files for a Power BI report and a web dashboard.

## The data

| Source | What I used |
| :- | :- |
| DfE, *Children in need* 2025 | Referrals and re-referrals, assessment duration, children in need at 31 March, child protection plans, repeat plans |
| DfE, *Children looked after in England including adoptions* 2025 | Rates of children in care, placement stability, care leavers' activity and accommodation |
| DfE, *Children's services statistical neighbour benchmarking tool* (May 2025 update) | The ten statistical neighbours for each borough |

All figures cover 2021 to 2025. The statistical neighbours used were:

* **Kingston:** Sutton, Merton, Hertfordshire, Bromley, Bath and North East Somerset, Windsor and Maidenhead, Trafford, Richmond upon Thames, Surrey, Buckinghamshire
* **Richmond:** Windsor and Maidenhead, Kingston upon Thames, Surrey, Wokingham, Bromley, Trafford, Buckinghamshire, Hertfordshire, Bath and North East Somerset, West Berkshire

## Results

### Kingston upon Thames, 2025

| Indicator | Kingston | Neighbours | Outer London | England | Verdict |
| :- | -: | -: | -: | -: | :- |
| Referrals per 10,000 children | 442 | 396 | 525 | 519 | Higher than neighbours |
| Re-referrals within 12 months | 15.0% | 19.0% | 19.6% | 22.6% | Better than neighbours |
| Assessments within 45 working days | 94.7% | 87.6% | 87.2% | 85.7% | Better than neighbours |
| Median assessment length | 43 days | 35 days | 32 days | 33 days | Higher than neighbours |
| Children in need per 10,000 | 270 | 272 | 327 | 330 | In line with neighbours |
| Children on a CP plan per 10,000 | 30 | 31 | 38 | 41 | In line with neighbours |
| CP plans that were a repeat plan | 17.3% | 23.2% | 19.3% | 24.5% | Better than neighbours |
| Children looked after per 10,000 | 30 | 42 | 43 | 67 | Lower than neighbours |
| Children in care with 3+ placements in the year | 7.1% | 8.8% | 10.4% | 10.4% | In line with neighbours |
| Long-term placement stability | 67.9% | 69.2% | 68.1% | 68.5% | In line with neighbours |
| Care leavers (19-21) in education, employment or training | – | 58.5% | 55.1% | 54.0% | No comparison |
| Care leavers (19-21) in suitable accommodation | 89.0% | 90.7% | 88.0% | 88.5% | In line with neighbours |

### Richmond upon Thames, 2025

| Indicator | Richmond | Neighbours | Outer London | England | Verdict |
| :- | -: | -: | -: | -: | :- |
| Referrals per 10,000 children | 324 | 406 | 525 | 519 | Lower than neighbours |
| Re-referrals within 12 months | 16.4% | 18.7% | 19.6% | 22.6% | Better than neighbours |
| Assessments within 45 working days | 94.9% | 87.8% | 87.2% | 85.7% | Better than neighbours |
| Median assessment length | 42 days | 35 days | 32 days | 33 days | Higher than neighbours |
| Children in need per 10,000 | 219 | 277 | 327 | 330 | Lower than neighbours |
| Children on a CP plan per 10,000 | 31 | 34 | 38 | 41 | In line with neighbours |
| CP plans that were a repeat plan | 20.8% | 23.2% | 19.3% | 24.5% | Better than neighbours |
| Children looked after per 10,000 | 27 | 44 | 43 | 67 | Lower than neighbours |
| Children in care with 3+ placements in the year | 7.4% | 8.8% | 10.4% | 10.4% | In line with neighbours |
| Long-term placement stability | 64.0% | 65.5% | 68.1% | 68.5% | In line with neighbours |
| Care leavers (19-21) in education, employment or training | 57.3% | 54.6% | 55.1% | 54.0% | Better than neighbours |
| Care leavers (19-21) in suitable accommodation | 92.3% | 90.9% | 88.0% | 88.5% | In line with neighbours |

"In line" means within 2 percentage points for percentages, or within 10% for rates and days.

### What stands out

* **Kingston's clearest strength is cp plans that were a repeat plan**: 17.3%, 5.9 percentage points below the neighbour average (23.2%).
* Kingston has 30 children looked after per 10,000, ranking 3 of 151 from lowest in England (England: 67).
* **Richmond's clearest strength is care leavers (19-21) in education, employment or training**: 57.3%, 2.7 percentage points above the neighbour average (54.6%).
* Richmond has 27 children looked after per 10,000, ranking 1 of 151 from lowest in England (England: 67).

![Five-year trends for Richmond](images/trends_richmond.png)

The full plain-English findings are in [insight_brief.md](insight_brief.md).

## What I learned, and how I'd interpret this

**The comparison group changes the story.** A figure that looks weak against England can look ordinary against statistical neighbours, and the reverse. Choosing the right comparator is the most important analytical decision in benchmarking, and it's worth explaining every time.

**Not every number is a target.** A low rate of children in care might reflect strong early help, or thresholds set too high. I labelled rates as *context* rather than good or bad, because treating demand measures as targets can push services in the wrong direction.

**Small numbers move a lot.** Both boroughs are small. A handful of children can shift a care leaver percentage by several points, so I always looked at five-year trends and the spread of neighbours before calling anything a strength or a concern.

**Getting the data right is most of the work.** DfE files changed format in 2025 (apprenticeships were split out of "training or employment"), some values are suppressed, and file names vary between releases. Building the pipeline to recognise data sets by their structure, and checking the England totals first, is what makes the results trustworthy.

**Benchmarking starts conversations.** The numbers tell a manager *where* to look, not *why*. The next step would always be talking to the teams behind the figures.

## Limitations

* Statistical neighbours match councils on population characteristics, not on how their services are organised.
* The neighbour average is a simple mean, so a very small neighbour counts as much as a very large one.
* Kingston and Richmond share a children's services provider, so differences between them reflect local demand and practice within one organisation.
* The most recent data is for the year ending 31 March 2025.

## Run it yourself

1. Download the two DfE "Download all data" zips and the statistical neighbour workbook (links in the notebook).
2. Open the notebook in Google Colab and select **Runtime > Run all**. Choose the three files when asked.

## Tools

Python (pandas, NumPy, Matplotlib), Power BI and DAX, Chart.js, Google Colab, GitHub Pages.

*Built by Sara Iqbal (MSc Data Science) as a portfolio project for data analyst roles in children's services. Contains public sector information licensed under the Open Government Licence v3.0.*
