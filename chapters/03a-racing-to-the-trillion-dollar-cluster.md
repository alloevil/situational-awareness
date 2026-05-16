---
title: "IIIa. Racing to the Trillion-Dollar Cluster"
author: "Leopold Aschenbrenner"
source: "https://situational-awareness.ai/racing-to-the-trillion-dollar-cluster/"
date: "June 2024"
---

**The most extraordinary techno-capital acceleration has been set in motion. As AI revenue grows rapidly, many trillions of dollars will go into GPU, datacenter, and power buildout before the end of the decade.  The industrial mobilization, including growing US electricity production by 10s of percent, will be intense. **

In this piece:

Toggle

* * *

> You see, I told you it couldn’t be done without turning the whole country into a factory. You have done just that.
>
> [Niels Bohr](<https://blog.nuclearsecrecy.com/2015/06/12/what-remains-of-the-manhattan-project/>) (to Edward Teller, upon learning of the scale of the Manhattan Project in 1944)

![figure](images/trillion_dollar_cluster-1024x585.png)_The trillion-dollar cluster. Credit: DALLE.  _

The race to AGI won’t just play out in code and behind laptops—it’ll be a race to mobilize America’s industrial might. Unlike anything else we’ve recently seen come out of Silicon Valley, AI is a massive industrial process: each new model requires a giant new cluster, soon giant new power plants, and eventually giant new chip fabs. The investments involved are staggering. But behind the scenes, they are already in motion.

In this post, I’ll walk you through numbers to give you a sense of what this will mean:

  * As revenue from AI products grows rapidly—plausibly hitting a $100B annual run rate for companies like Google or Microsoft by ~2026, with powerful but pre-AGI systems—that will motivate ever-greater capital mobilization, and total AI investment could be north of $1T _annually_ by 2027.
  * We’re on the path to individual training clusters costing $100s of billions by 2028—clusters requiring power equivalent to a small/medium US state and more expensive than the International Space Station.
  * By the end of the decade, we are headed to $1T+ individual training clusters, requiring power equivalent to >20% of US electricity production. Trillions of dollars of capex will churn out 100s of millions of GPUs per year overall.


Nvidia shocked the world as its datacenter sales exploded from about [$14B annualized](<https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-fourth-quarter-and-fiscal-2023>) to about [$90B annualized](<https://nvidianews.nvidia.com/news/nvidia-announces-financial-results-for-first-quarter-fiscal-2025>) in the last year. But that’s still just the very beginning.

## **Training compute**

[Earlier](<https://situational-awareness.ai/from-gpt-4-to-agi/#Compute>), we found a roughly ~0.5 OOMs/year trend growth of AI training compute.1 If this trend were to continue for the rest of the decade, what would that mean for the largest training clusters?

Year| OOMs| **# of H100s-** equivalent     | Cost| Power| Power reference class
---|---|---|---|---|---
2022| ~GPT-4 cluster| ~10k| ~$500M| ~10 MW| ~10,000 average homes
~2024| +1 OOM| ~100k| $billions| ~100MW| ~100,000 homes
~2026| +2 OOMs| ~1M| $10s of billions| ~1 GW| The Hoover Dam, or a large nuclear reactor
~2028| +3 OOMs| ~10M| $100s of billions| ~10 GW| A small/medium US state
~2030| +4 OOMs| ~100M| $1T+| ~100GW| >20% of US electricity production
 _Scaling the largest training clusters, rough back-of-the-envelope calculations._

####  [ __Details on the calculations for the largest training clusters](<javascript:void\(0\)>)

**Year
**The [OpenAI GPT-4 tech report](<https://arxiv.org/pdf/2303.08774>) stated that GPT-4 finished training in August 2022. Thereafter we play forward the rough ~0.5 OOMs/year trend.



**H100s-equivalent
**[Semianalysis](<https://www.semianalysis.com/p/gpt-4-architecture-infrastructure%5C>), [JP Morgan](<https://colab.research.google.com/drive/1O99z9b1I5O66bT78r9ScslE_nOj5irN9>), and others estimate GPT-4 was trained on ~25k A100s, and H100s are 2-3x the performance of A100s.



**Cost
**Often people cite numbers like “$100M for GPT-4 training,” using just the rental cost of the GPUs (i.e., something like “how much would it cost to rent this size cluster for 3 months of training). But that’s a mistake. What matters is something more like ~the actual cost to build the cluster. If you want one of the largest clusters in the world, you can’t just rent it for 3 months! And moreover, you need the compute for more than just the flagship training run: there will be lots of derisking experiments, failed runs, other models, etc.

To approximate the GPT-4 cluster cost:

  * The [public](<https://www.semianalysis.com/p/gpt-4-architecture-infrastructure%5C>) [estimates](<https://colab.research.google.com/drive/1O99z9b1I5O66bT78r9ScslE_nOj5irN9>) suggest the GPT-4 cluster being around 25k A100s.
  * Assuming $1/A100-hour for 2-3 years gives roughly a $500M cost.
  * Alternatively, you can estimate it as ~$25k cost per H100, 10k H100s-equivalent, and Nvidia GPUs being around ~half the cost of a cluster (the rest being power, the physical datacenter, cooling, networking, maintenance personnel, etc.).
    * (For example, this [total-cost-of-ownership analysis](<https://pytorchtoatoms.substack.com/p/metas-24k-h100-cluster-capextco-and>) estimates that around 40% of a large cluster cost is the H100 GPUs itself, and another 13% goes to Nvidia for Infiniband networking. That said, excluding cost of capital in that calculation would mean the GPUs are about 50% of the cost, and with networking Nvidia gets a bit over 60% of the cost of the cluster.)


_FLOP/$_ is improving somewhat for each Nvidia generation, but not a ton. E.g., the H100 -> B100 is likely something like 1.5x FLOP/$: B100s are effectively two H100s stapled together, but retailing for <2x the cost. But the B100 was somewhat of an exception. They are surprisingly cheap, likely because Nvidia [wants to crush competition](<https://www.semianalysis.com/p/nvidia-b100-b200-gb200-cogs-pricing>). By contrast, A100s -> H100s weren’t much of a FLOP/$ improvement (2x better chip without fp8, roughly 2x the cost), maybe 1.5x if we count fp8 improvements—and that was for a two-year generation.

While I think there are some tailwinds to further FLOP/$ improvements from margin compression, GPUs might also get more expensive as they become massively constrained. Gains from AI chip specialization will continue, but it’s not clear to me there will still be game-changing technical improvements to FLOP/$ coming, given chips are already pretty specialized for AI (e.g. specialized for Transformers, and already at fp8/fp4 precision), Moore’s Law is glacial these days, and [other bottleneck components like memory and interconnect are improving more slowly](<https://twitter.com/karpathy/status/1691571869051445433>). If you look at [Epoch’s data](<https://epochai.org/blog/trends-in-gpu-price-performance>), there seems to be less than a 10x in FLOP/$ over the past decade for top ML GPUs, and for the aforementioned reasons if anything I’d expect this to slow down.

Something like a 35%/year improvement in FLOP/$ would give us the 1T cost for the +4 OOM cluster. Maybe FLOP/$ improves faster, but also datacenter capex is going to get more expensive—simply because you’ll need to actually build new power, doing a lot of capex up front, rather than just renting existing depreciated power plants.

These are just very rough numbers anyway. It would be very much within error bars if e.g. the 1T cluster can be done more efficiently and actually yields more like +4.5 OOMs on compute.



**Power requirements
**An H100 is 700W, but there’s a bunch of datacenter power you need (cooling, networking, storage); Semianalysis [estimates](<https://www.semianalysis.com/p/ai-datacenter-energy-dilemma-race> "estimates") ~1,400W per H100.

There are some gains to be had on FLOP/Watt, though once we’ve exhausted the gains from AI chip specialization (see previous footnote), e.g. gone down to the lowest possible precision, these seem somewhat limited (mostly just chip process improvements, which are slow). That said, as power becomes more of a constraint (and thus a larger fraction of costs), chip designs might specialize to more power-efficiency at the costs of FLOPs. Still, there is still the power demand for cooling, networking, storage, and so on (which in the H100 numbers above was already roughly half the power demand).

For these back of the envelope numbers, let’s work with 1kW per H100-equivalent here; again these are just rough back-of-the-envelope calculations. (And if there were an unexpected FLOP/Watt breakthrough, I’d expect the same power expenditure, just bigger OOM compute gains.)



**Power reference classes
**A 10GW cluster run continuously for a year is 87.6 TWh. By comparison, Oregon [consumes about 27 TWh](<https://www.energy.gov/sites/prod/files/2016/09/f33/OR_Energy%20Sector%20Risk%20Profile.pdf>) of electricity annually, Washington state [consumes about 92 TWh annually](<https://www.energy.gov/sites/prod/files/2016/09/f33/WA_Energy%20Sector%20Risk%20Profile.pdf>).

A 100GW cluster run continuously for a year is 876 TWh, while total annual US electricity production is about 4,250 TWh.

This may seem hard to believe—but it appears to be happening. Zuck [bought 350k H100s](<https://www.cnbc.com/2024/01/18/mark-zuckerberg-indicates-meta-is-spending-billions-on-nvidia-ai-chips.html>). Amazon [bought a 1GW datacenter campus](<https://www.datacenterdynamics.com/en/news/aws-acquires-talens-nuclear-data-center-campus-in-pennsylvania/>) next to a nuclear power plant. Rumors [suggest](<https://twitter.com/rediminds/status/1749852816938529247?lang=en>) a 1GW, 1.4M H100-equivalent cluster (~2026-cluster) is being built in Kuwait. Media report that [Microsoft and OpenAI are rumored to be working on a $100B cluster, slated for 2028](<https://www.reuters.com/technology/microsoft-openai-planning-100-billion-data-center-project-information-reports-2024-03-29/>) (a cost comparable to the [International Space Station](<https://en.wikipedia.org/wiki/International_Space_Station_programme#:~:text=Cost,-This%20section%20is&text=The%20ISS%20has%20been%20described,cost%20was%20US%24150%20billion.>)!). And as each generation of models shocks the world, further acceleration may yet be in store.

Perhaps the wildest part is that willingness-to-spend doesn’t even seem to be the binding constraint at the moment, at least for training clusters. It’s finding the infrastructure itself: “Where do I find 10GW?” (power for the $100B+, trend 2028 cluster) is a favorite topic of conversation in SF. What any compute guy is thinking about is securing power, land, permitting, and datacenter construction.2 While it may take you a year of waiting to get the GPUs, the lead times for these are much longer still.

The trillion-dollar cluster—+4 OOMs from the GPT-4 cluster, the ~2030 training cluster on the current trend—will be a truly extraordinary effort. The 100GW of power it’ll require is equivalent to >20% of US electricity production; imagine not just a simple warehouse with GPUs, but hundreds of power plants. Perhaps it will take a national consortium.

(Note that I think it’s pretty likely we’ll only need a ~$100B cluster, or less, for AGI. The $1T cluster might be what we’ll train and run superintelligence on, or what we’ll use for AGI if AGI is harder than expected. In any case, in a post-AGI world, having the most compute will probably still really __ matter.)

## **Overall compute**

The above are just rough numbers for the largest training clusters. Overall investment is likely to be much larger still: a large fraction of GPUs will probably be used for inference3 (GPUs to actually run the AI systems for products), and there could be multiple players with giant clusters in the race.

My rough estimate is that 2024 will already feature $100B-$200B of AI investment:

  * Nvidia datacenter revenue will hit a ~$25B/quarter run rate soon, i.e. ~$100B of capex flowing via Nvidia alone. But of course, Nvidia isn’t the only player (Google’s TPUs are great too!), and close to half of datacenter capex is on things other than the chips (site, building, cooling, power, etc.)4

![figure](images/nvida_datacenter_revenue.png)_Quarterly Nvidia datacenter revenue. Plot by_[ _Thomas Woodside_](<https://twitter.com/Thomas_Woodside/status/1795247239990014409/photo/1>).

  * Big tech has been dramatically ramping their capex numbers: Microsoft and Google will likely do $50B+,5 AWS and Meta $40B+, in capex this year. Not all of this is AI, but combined their capex will have grown $50B-100B year-over-year because of the AI boom, and even then they are still cutting back on other capex to shift even more spending to AI. Moreover, other cloud providers, companies (e.g., [Tesla is spending $10B](<https://twitter.com/heyitsyashu/status/1784594856037208516?s=12>) on AI this year), and nation-states are investing in AI as well.


![figure](images/big_tech_capex.jpg)_Big tech capex is growing extremely rapidly since ChatGPT unleashed the AI boom._[_Graphic source_](<https://basehitinvesting.substack.com/p/big-tech-capex-and-earnings-quality>) _._

Let’s play this forward. My best guess is overall compute investments will grow more slowly than the 3x/year largest training clusters, let’s say 2x/year.6

Year| Annual investment| AI accelerator shipments (in H100s-equivalent)| Power as % of US electricity production
7  | Chips as % of current leading-edge TSMC wafer production
---|---|---|---|---
2024| ~$150B| ~5-10M 8| 1-2%| 5-10%9
~2026| ~$500B| ~10s of millions| 5%| ~25%
~2028| ~$2T| ~100M| 20%| ~100%
~2030| ~$8T| Many 100s of millions | 100%| 4x current capacity
 _Playing forward trends on total world AI investment. Rough back-of-the-envelope calculation.  _

And these aren’t just my idiosyncratic numbers. [AMD forecasted](<https://www.bloomberg.com/news/articles/2023-12-06/amd-ceo-debuts-new-nvidia-chip-rival-gives-eye-popping-forecast?embedded-checkout=true>) a $400B AI accelerator market by 2027, implying $700B+ of total AI spending, pretty close to my numbers (and they are surely much less “AGI-pilled” than I am). Sam Altman is reported to be in talks to raise funds for a project of “[up to $7T](<https://www.wsj.com/tech/ai/sam-altman-seeks-trillions-of-dollars-to-reshape-business-of-chips-and-ai-89ab3db0>)” in capex to build out AI compute capacity (the number was widely mocked, but it seems less crazy if you run the numbers here…). One way or another, this massive scaleup is happening.

## **Will it be done? Can it be done?**

The scale of investment postulated here may seem fantastical. But both the demand-side and the supply-side seem like they could support the above trajectory. The economic returns justify the investment, the scale of expenditures is not unprecedented for a new general-purpose technology, and the industrial mobilization for power and chips is doable.

### **AI revenue  **

Companies will make large AI investments if they expect the economic returns to justify it.

Reports suggest OpenAI was at a $1B revenue run rate in [August 2023](<https://www.theinformation.com/articles/openai-passes-1-billion-revenue-pace-as-big-companies-boost-ai-spending>), and a $2B revenue run rate in [February 2024](<https://www.reuters.com/technology/openai-hits-2-bln-revenue-milestone-ft-2024-02-09/>). That’s roughly a doubling every 6 months. If that trend holds, we should see a ~$10B annual run rate by late 2024/early 2025, even without pricing in a massive surge from any next-generation model. One estimate puts [Microsoft](<https://x.com/ttunguz/status/1783941512159776840>) at ~$5B of incremental AI revenue already.

So far, every 10x scaleup in AI investment seems to yield the necessary returns. GPT-3.5 unleashed the ChatGPT mania. The estimated $500M cost for the GPT-4 cluster would have been paid off by the reported billions of annual revenue for Microsoft and OpenAI (see above calculations), and a “2024-class” training cluster in the billions will easily pay off if Microsoft/OpenAI AI revenue continues on track to a $10B+ revenue run rate. The boom is investment-led: it takes time from a huge order of GPUs to build the clusters, build the models, and roll them out, and the clusters being planned today are many years out. But if the returns on the last GPU order keep materializing, investment will continue to skyrocket (and outpace revenue), plowing in even more capital in a bet that the next 10x will keep paying off.

A key milestone for AI revenue that I like to think about is: when will a big tech company (Google, Microsoft, Meta, etc.) hit a $100B revenue run rate from AI (products and API)? These companies have on the order of $100B-$300B of revenue today; $100B would thus start representing a very substantial fraction of their business. Very naively extrapolating out the doubling every 6 months, supposing we hit a $10B revenue run rate in early 2025, suggests this would happen mid-2026.

That may seem like a stretch, but it seems to me to require surprisingly little imagination to reach that milestone. For example, there are around [350 million paid subscribers to Microsoft Office](<https://office365itpros.com/2022/04/28/office-365-number-of-users/>)—could you get a third of these to be willing to pay $100/month for an AI add-on? For an average worker, that’s only a few hours a month of productivity gained; models powerful enough to make that justifiable seem very doable in the next couple years.10

It’s hard to understate the ensuing reverberations. This would make AI products the biggest revenue driver for America’s largest corporations, and _by far_ their biggest area of growth. Forecasts of overall revenue growth for these companies would skyrocket. Stock markets would follow; we might see our first $10T company soon thereafter. Big tech at this point would be willing to go all out, each investing many hundreds of billions (at least) into further AI scaleout. We probably see our first many-hundred-billion dollar corporate bond sale then.11

Beyond $100B, it gets harder to see the contours. But if we are truly on the path to AGI, the returns will be there. White-collar workers are paid tens of trillions of dollars in wages annually worldwide; a drop-in remote worker that automates even a fraction of white-collar/cognitive jobs (imagine, say, a truly automated AI coder) would pay for the trillion-dollar cluster. If nothing else, the national security import could well motivate a government project, bundling the nation’s resources in the race to AGI ([more later](<https://situational-awareness.ai/the-project/>)).

### **Historical precedents**

$1T/year of total annual AI investment by 2027 seems outrageous. But it’s worth taking a look at other historical reference classes:

  * In their peak years of funding, the Manhattan and Apollo programs [reached 0.4% of GDP](<https://sgp.fas.org/crs/misc/RL34645.pdf>), or ~$100 billion annually today (surprisingly small!). At $1T/year, AI investment would be about 3% of GDP.
  * Between 1996–2001, [telecoms invested](<https://www.latimes.com/archives/la-xpm-2002-jun-30-fi-billions30-story.html>) nearly $1 trillion in today’s dollars in building out internet infrastructure.
  * From 1841 to 1850, [private British railway investments totaled](<https://x.com/michael_nielsen/status/1782129830932210166>) a cumulative ~40% of British GDP at the time. A similar fraction of [US GDP](<https://fred.stlouisfed.org/series/GDP>) would be equivalent to ~$11T over a decade.
  * [Many trillions](<https://www2.deloitte.com/content/dam/Deloitte/global/Documents/deloitte-financing-the-green-energy-transition-report-2023.pdf>) are being spent on the green transition.
  * Rapidly-growing economies often spend a high fraction of their GDP on investment; for example, China has spent more than [40% of its GDP on investment for two decades](<https://carnegieendowment.org/chinafinancialmarkets/91161#:~:text=It%20currently%20invests%2042%E2%80%9344,percent%20in%202010%20and%202011>) (equivalent to $11T _annually_ given US GDP).
  * In the historically most exigent national security circumstances—wartime—borrowing to finance the national effort has often comprised enormous fractions of GDP. During WWI, the [UK](<https://bankunderground.co.uk/2017/08/08/your-country-needs-funds-the-extraordinary-story-of-britains-early-efforts-to-finance-the-first-world-war/>) and [France](<https://encyclopedia.1914-1918-online.net/article/war_finance_france>), and [Germany](<https://encyclopedia.1914-1918-online.net/article/war_finance_germany>) borrowed over 100% of their GDPs while the [US](<https://www.theatlantic.com/business/archive/2012/11/the-long-story-of-us-debt-from-1790-to-2011-in-1-little-chart/265185/>) borrowed over 20%; during WWII, the [UK](<https://obr.uk/box/post-world-war-ii-debt-reduction/>) and Japan borrowed over 100% of their GDPs while the [US](<https://www.theatlantic.com/business/archive/2012/11/the-long-story-of-us-debt-from-1790-to-2011-in-1-little-chart/265185/>) borrowed over 60% of GDP (equivalent to over $17T today).


$1T/year of total AI investment by 2027 would be dramatic—among the very largest capital buildouts ever—but would not be unprecedented. And a trillion-dollar individual training cluster by the end of the decade seems on the table.12

### **Power**

Probably the single biggest constraint on the supply-side will be [power](<https://www.wsj.com/business/energy-oil/big-techs-latest-obsession-is-finding-enough-energy-f00055b2>). Already, at nearer-term scales (1GW/2026 and especially 10GW/2028), power has become the binding constraint: there simply isn’t much spare capacity, and power contracts are usually long-term locked-in. And building, say, a new gigawatt-class nuclear power plant takes a decade. (I’ll wonder when we’ll start seeing things like tech companies buying [aluminum smelting companies](<https://en.wikipedia.org/wiki/Aluminerie_Alouette>) for their gigawatt-class power contracts.13)

![figure](images/us_power-1024x790.png)_Comparing trends on total US electricity production to our rough back of the envelope estimates on AI electricity demands._

Total US electricity generation has [barely grown 5% in the last decade](<https://en.wikipedia.org/wiki/Electricity_sector_of_the_United_States>).14 Utilities are [starting to get excited](<https://twitter.com/hayekandkeynes/status/1776365744323780997?s=12>) about AI ([instead of](<https://www.wsj.com/business/energy-oil/data-centers-energy-georgia-development-7a5352e9?st=gi5gnqcodm9uy16>) 2.6% growth over the next 5 years, they now estimate 4.7%!). But they’re barely pricing in what’s coming. The trillion-dollar, 100GW cluster alone would require ~20% of current US electricity generation in 6 years; together with large inference capacity, demand will be multiples higher.

To most, this seems completely out of the question. Some are betting on Middle Eastern autocracies, who have been going around offering boundless power and giant clusters to get their rulers a seat at the AGI-table.

But it’s totally possible to do this in the United States: we have abundant natural gas.15

  * Powering a 10GW cluster would take only a few percent of US natural gas production and could be done rapidly.
  * Even the 100GW cluster is surprisingly doable.
    * Right now the Marcellus/Utica shale (around Pennsylvania) alone is [producing](<https://www.eia.gov/petroleum/drilling/pdf/appalachia.pdf>) around 36 billion cubic feet a day of gas; that would be enough to generate just under 150GW continuously with generators (and combined cycle power plants could output 250 GW due to their higher efficiency).
    * It would take about ~1200 [new wells](<https://ir.rangeresources.com/static-files/cd9b4c2c-f4fe-4118-9659-a4c3528b95b1>) for the 100GW cluster.16 Each rig can drill roughly 3 wells per month, so 40 rigs (the current [rig count](<https://www.eia.gov/petroleum/drilling/pdf/appalachia.pdf>) in the Marcellus) could build up the production base for 100GW in less than a year.17The Marcellus had a rig count of ~80 as recently as 2019 so it would not be taxing to add 40 rigs to build up the production base.18
    * More generally, US natural gas production has more than [doubled in a decade](<https://en.wikipedia.org/wiki/Shale_gas_in_the_United_States#/media/File:Shale_gas_production_USA.svg>); simply continuing that trend could power multiple trillion-dollar datacenters.19
    * The harder part would be building enough generators/turbines; this wouldn’t be trivial, but it seems doable with about $100B of capex20 for 100GW of natural gas power plants. Combined cycle plants can be built in about two years; the timeline for generators would be even shorter still.21


The barriers to even trillions of dollars of datacenter buildout in the US are entirely self-made. Well-intentioned but rigid climate commitments (not just by the government, but green datacenter commitments by Microsoft, Google, Amazon, and so on) stand in the way of the obvious, fast solution. At the very least, even if we won’t do natural gas, a broad deregulatory agenda would unlock the solar/batteries/SMR/geothermal megaprojects. Permitting, utility regulation, FERC regulation of [transmission lines](<https://ifp.org/how-cost-allocation-works-for-transmission-lines/>), and NEPA environmental review makes things that should take a few years take a decade or more. We don’t have that kind of time.

We’re going to drive the AGI datacenters to the Middle East, under the thumb of brutal, capricious autocrats. I’d prefer clean energy too—but this is simply too important for US national security. We will need a new level of determination to make this happen. The power constraint can, must, and will be solved.

### **Chips**

While chips are usually what comes to mind when people think about AI-supply-constraints, they’re likely a smaller constraint than power. Global production of AI chips is still a pretty small percent of TSMC-leading-edge production, likely less than 10%. There’s a lot of room to grow via AI becoming a larger share of TSMC production.

Indeed, 2024 production of AI chips (~5-10M H100-equivalents) would already be almost enough for the $100s of billion cluster (if they were all diverted to one cluster). From a pure logic fab standpoint ~100% of TSMC’s output for a year could already support the trillion-dollar cluster (again if all the chips went to one datacenter).22 Of course, not all of TSMC will be able to be diverted to AI, and not all of AI chip production for a year will be for one training cluster. Total AI chip demand (including inference and multiple players) by 2030 will be a multiple of TSMC’s current total leading-edge logic chip capacity, just for AI. TSMC ~[doubled](<https://www.macrotrends.net/stocks/charts/TSM/taiwan-semiconductor-manufacturing/revenue>)23 in the past 5 years; they’d likely need to go ~at least twice as fast on their pace of expansion to meet AI chip demand. Massive new fab investments would be necessary.

Even if raw logic fabs won’t be the constraint, chip-on-wafer-on-substrate (CoWoS) advanced packaging (connecting chips to memory, also made by TSMC, Intel, and others) and HBM memory (for which demand [is](<https://twitter.com/ericjhonsa/status/1770545692978925955?s=12>) [enormous](<https://twitter.com/dnystedt/status/1787662436478410867?s=12>)) are already key bottlenecks for the current AI GPU scaleup; these are more specialized to AI, unlike the pure logic chips, so there’s less pre-existing capacity. In the near term, these will be the primary constraint on churning out more GPUs, and these will be the huge constraints as AI scales. Still, these are comparatively “easy” to scale; it’s been incredible watching TSMC literally build “greenfield” fabs (i.e. entirely new facilities from scratch) to massively scale up CoWoS production this year (and Nvidia is even starting to find [CoWoS alternatives](<https://x.com/dnystedt/status/1793096268400759110?s=46&t=EfdUOH7OfS4lpc8-o1U6Dg>) to work around the shortage).

A new TSMC [Gigafab](<https://www.asianometry.com/p/the-economics-of-tsmcs-giga-fabs>) (a [technological marvel](<https://www.construction-physics.com/p/how-to-build-a-20-billion-semiconductor>)) costs around $20B in capex and produces 100k wafer-starts a month. For hundreds of millions of AI GPUs a year by the end of the decade, TSMC would need to build dozens of these—as well as a huge buildout for memory, advanced packaging, networking, etc., which will be a major fraction of capex. It could add up to over $1T of capex. It will be intense, but doable. (Perhaps the biggest roadblock will not be feasibility, but TSMC not even trying—TSMC does not yet seem AI-scaling-pilled! They think AI will “only” grow at a [glacial 50% CAGR](<https://www.fierceelectronics.com/ai/tsmc-bullish-ai-q1-revenues-rises-q2-outlook-bright>).)

Recent USG efforts like the CHIPS Act have been trying to onshore more AI chip production to the US (as insurance in case of the Taiwan contingency). While onshoring more of AI chip production to the US would be nice, it’s less critical than having the actual datacenter (on which the AGI lives) in the US. If having chip production abroad is like having uranium deposits abroad, having the AGI datacenter abroad is like having the literal nukes be built and stored abroad. Given the dysfunction and cost we’ve seen from building fabs in the US in practice, my guess is we should prioritize datacenters in the US while betting more heavily on democratic allies like Japan and South Korea for fab projects—fab buildouts there [seem much more functional](<https://twitter.com/dnystedt/status/1768446340881907914?s=12>).

## **The Clusters of Democracy**

Before the decade is out, many trillions of dollars of compute clusters will have been built. The only question is whether they will be built in America. Some are rumored to be betting on building them elsewhere, especially in the Middle East. Do we really want the infrastructure for the Manhattan Project to be controlled by some capricious Middle Eastern dictatorship?

The clusters that are being planned today may well be the clusters AGI and superintelligence are trained and run on, not just the “cool-big-tech-product clusters.”  The national interest demands that these are built in America (or close democratic allies). Anything else creates an irreversible security risk: it risks the AGI weights getting stolen24 (and perhaps be [shipped to China](<https://www.nytimes.com/2023/11/27/us/politics/ai-us-uae-china-security-g42.html>)) ([more later](<https://situational-awareness.ai/lock-down-the-labs/>)); it risks these dictatorships physically seizing the datacenters (to build and run AGI themselves) when the AGI race gets hot; or even if these threats are only wielded implicity, it puts AGI and superintelligence at unsavory dictator’s whims. America sorely regretted her energy dependence on the Middle East in the 70s, and we worked so hard to get out from under their thumbs. We cannot make the same mistake again.

The clusters can be built in the US, and we have to get our act together to make sure it happens in the US. American national security must come first, before the allure of free-flowing Middle Eastern cash, arcane regulation, or even, yes, admirable climate commitments. We face a real system competition—can the requisite industrial mobilization only be done in “top-down” autocracies? If American business is unshackled, America can build like none other (at least in red states). Being willing to use natural gas, or at the very least a broad-based deregulatory agenda—NEPA exemptions, fixing FERC and transmission permitting at the federal level, overriding utility regulation, using federal authorities to unlock land and rights of way—is a national security priority.

* * *

In any case—the exponential is in full swing now.

In the “old days,” when AGI was still a dirty word, some colleagues and I used to make theoretical economic models of what the path to AGI might look like. One feature of these models used to be a hypothetical “AI wakeup” moment, when the world started realizing how powerful these models could be and began rapidly ramping up their investments—culminating in multiple % of GDP towards the largest training runs.

It seemed far-off then, but that time has come. 2023 _was_ “AI wakeup.”25 Behind the scenes, the most staggering techno-capital acceleration has been put into motion.

Brace for the G-forces.

Next post in series:
_[**IIIb. Lock Down the Labs: Security for AGI**](<https://situational-awareness.ai/lock-down-the-labs/>)_

_(What all of this means for NVDA/TSM/etc. I leave as an exercise for the reader. Hint: Those with situational awareness bought much lower than you, but it’s still not even close to fully priced in._26 _)_

* * *

  1. As mentioned,  OOM = order of magnitude, 10x = 1 order of magnitude↩

  2. One key uncertainty is how distributed training will be—if instead of needing that amount of power in one location, we could spread it among 100 locations, it’d be a lot easier.↩

  3. See, for example, Zuck [here](<https://x.com/akhenosiris/status/1781162128881164566>); only ~45k of his H100s are in his largest training clusters, the vast majority of his 350k H100s for inference. Meta likely has heavier inference needs than other players, who serve fewer customers so far, but as everyone else’s AI products scale, I expect inference to become a strong majority of the GPUs.↩

  4. For example, this [total-cost-of-ownership analysis](<https://pytorchtoatoms.substack.com/p/metas-24k-h100-cluster-capextco-and>) estimates that around 40% of a large cluster cost is the H100 GPUs itself, and another 13% goes to Nvidia for Infiniband networking. That said, excluding cost of capital in that calculation would mean the GPUs are about 50% of the cost, and with networking would mean Nvidia gets a bit over 60% of the cost of the cluster.↩

  5. And [apparently](<https://www.cnbc.com/2024/04/25/microsoft-says-cloud-ai-demand-exceeds-supply-despite-spending-surge.html>), despite Microsoft growing capex by 79% compared to a year ago in a recent quarter, their AI cloud demand still exceeds supply!↩

  6. A larger fraction of global GPU production will probably be going to the largest training cluster in the future than today, e.g. because of a consolidation to just a few leading labs, rather than many companies having frontier-model-scale clusters.↩

  7. Of course, not all of this will be in the US, but to give a reference class.↩

  8. I estimate Nvidia is going to ship on the order of 5M datacenter GPUs in 2024. A minority of those are B100s, which we’ll count as 2x+ H100s. Then there’s the other AI chips: TPUs, Trainium, Meta’s custom silicon, AMD GPUs, etc.↩

  9. TSMC has capacity for over [150k 5nm](<https://wccftech.com/tsmc-boosts-5nm-production-to-150000-wafers-month-amidst-strong-demand/#:~:text=The%20DigiTimes%20report%20is%20quite,mark%20a%2025%25%20production%20increase.>) wafers per month, is ramping to [100k 3nm wafers](<https://wccftech.com/tsmc-3nm-wafer-production-reaching-100000-units-by-end-of-2024/>) per month, and likely another [150k or so](<https://www.digitimes.com/news/a20200902PD200.html>) 7nm wafers per month; let’s call it 400k wafers per month in total.

Let’s say roughly [35 H100s per wafer](<https://www.reddit.com/r/AMD_Stock/comments/18es0ks/amd_can_get_65_more_mi300x_from_the_same_5nm/>) (H100s are made on 5nm). At 5-10 million H100-equivalents in 2024, that’s 150k-300k wafers per year for annual AI chip production in 2024.

Depending on where in that range and whether we want to count 7nm production, that’s about 3-10% of annual leading-edge wafer production.↩

  10. A big uncertainty for me is what the lags are for the technology to diffuse and be adopted. I think it’s plausible revenue is slowed because intermediate, pre-AGI models take a lot of “schlep” to properly integrate into company workflows; historically, it’s taken a while to fully harvest the productivity gains from new general purpose technologies. This is where the “[sonic boom](<https://situational-awareness.ai/from-gpt-4-to-agi/#sonic_boom> "sonic boom")” discussion earlier comes in: as we “unhobble” models and they start looking more like agents/drop-in remote workers,, deploying them becomes much easier. Rather than having to completely remake some workflow to harvest a 25% productivity gain from a GPT-chatbot, instead you’ll get models that you can onboard and work with as you would a new coworker (e.g., just directly substitute for an engineer, rather than needing to train up engineers to use some new tool). Or, in the extreme, and later on: you won’t need to completely redesign a factory to work with some new tool, you’ll just bring in the humanoid robots.

That said, this may lead to some discontinuity in economic value and revenue generated, depending on how quickly we can “unhobble” models.↩

  11. What will happen to interest rates will be interesting… see [Tyler Cowen here](<https://www.bloomberg.com/opinion/articles/2024-03-27/ai-could-have-a-surprising-effect-on-interest-rates?sref=o4HC3q1q>); [Chow, Mazlish and Halperin here](<https://basilhalperin.com/papers/agi_emh.pdf>).↩

  12. And, farther out, but if AGI truly led to substantial increases in economic growth, $10T+ annually would start being plausible—the reference class being investment rates of countries during high-growth periods.↩

  13.  “Since 2011, the Alouette Smelter uses 930 MW electricity at maximum production capacity.”↩

  14. That said, this is “net-new” capacity: some of that is building new renewables and taking old fossil fuel plants off the grid. Maybe it’s closer to a percent or two a year of gross-new capacity.↩

  15. Thanks to [Austin Vernon](<https://austinvernon.site/>) (private correspondence) for helping with these estimates.↩

  16. New wells produce around 0.01 BCF per day.↩

  17.  Each well produces ~20 BCF over its lifetime, meaning two new wells a month would replace the depleted reserves, i.e. it would need only one rig to maintain the production.↩

  18.  Though it would be more efficient to add less rigs and build up over a longer time frame than 10 months.↩

  19. A cubic foot of natural gas [generates about](<https://www.eia.gov/tools/faqs/faq.php?id=667&t=6>) 0.13 kWh. Shale gas production [was about](<https://en.wikipedia.org/wiki/Shale_gas_in_the_United_States#/media/File:Shale_gas_production_USA.svg>) ~70 billion cubic feet per day in the US in 2020. Suppose we doubled production again, and the extra capacity all went to compute clusters. That’s 3322 TWh/year of electricity, or enough for almost 4 100GW clusters.↩

  20. The capex costs for natural gas power plants [seem to be ](<https://atb-archive.nrel.gov/electricity/2019/index.html?t=cg>)under $1000 per kW, meaning the capex for 100GW of natural gas power plants would be about $100 billion.↩

  21. Solar and batteries aren’t a totally crazy alternative, but it does just seem rougher than natural gas. I did appreciate [Casey Handmer’s calculation](<https://caseyhandmer.wordpress.com/2024/03/12/how-to-feed-the-ais/>) of tiling the Earth in solar panels:
“With current GPUs, the global solar datacenter’s compute is equivalent to ~150 billion humans, though if our computers can eventually match [human brain] efficiency, we could support more like 5 quadrillion AI souls.”↩

  22.  This poses the interesting question of why power requirements are going up so much before chip fab production starts being really constrained. A simple answer is while datacenters run continuously at close to max power, most chips currently produced are idle a lot of the time. Currently, smartphones are close to half of leading chip demand, but use a lot less energy per wafer area (trading transistors for serial operations and energy efficiency) and have low utilization as smartphones are mostly idle. The AI revolution means working our transistors way harder, dedicating them all to constantly-running, high-performance AI datacenters instead of idle, battery-powered/energy-saving devices. HT Carl Shulman for this point.↩

  23. (Using revenue as a proxy.)↩

  24.  It’s a lot easier to do side-channel attacks to exfiltrate weights with physical access!↩

  25. I distinctly remember writing “THE TAKEOFF HAS STARTED” on my whiteboard in March of 2023.↩

  26. Mainstream sell-side analysts seem to assume only 10-20% year-over-year growth in Nvidia revenue from CY24 to CY25, maybe $120B-$130B in CY25 (or at least did until very recently). Insane! It’s been pretty obvious for a while that Nvidia is going to do over $200B of revenue in CY25.↩
