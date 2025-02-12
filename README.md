
![topbanner](https://github.com/user-attachments/assets/83515454-e562-47d5-bc08-ed67220c7499)

# Business Intelligence Case Study: Google Fiber

In this case study, I will tackle a business intelligence project from beginning to end. In addition to this overview, I've created several deliverables including project planning documents, a responsive dashboard, and an executive slide deck summarizing my findings.

## Project Deliverables
#### **Project Planning Docs**
* [Stakeholder Requirements Document](https://github.com/Geno2K/case-study-fiber/blob/main/Google%20Fiber%20Stakeholder%20Requirements%20Document.md)
* [Project Requirements Document](https://github.com/Geno2K/case-study-fiber/blob/main/Google%20Fiber%20Project%20Requirements%20Document.md)
* [Strategy Document](https://github.com/Geno2K/case-study-fiber/blob/main/Google%20Fiber%20Strategy%20Document.md)
#### **Dashboard**
* [Dashboard](https://public.tableau.com/app/profile/tommy.demos/viz/GoogleFiber_17393798674430/GoogleFiberCallCenterAnalytics?publish=yes)
#### Slide Deck
* [Slide Deck](https://docs.google.com/presentation/d/e/2PACX-1vR0tlUPoulYz_6xCt9QsoNb6Z_9U8spE5vhzvjjV8AyqZSAzNN7ZZCxyp_-kRy_nfw-LjtCLKlo6aVU/pub?start=false&loop=false&delayms=5000)
## Scenario:

In this fictional scenario, I am tackling a BI Project for the Google Fiber Customer service team as an applicant for the company's business intelligence team. They are experiencing a high volume of repeat customer service calls at their call centers and would like me to take a look at the data and produce a dashboard that could help them find insights, implement solutions, and track their progress over time.

Project stakeholders include the hiring manager, project manager, lead BI analyst, and additional BI team members. The dashboard and other deliverables will be for internal use only and have standard accessibility requirements (large print and text to speech options available).

## Business Task:

> Create a responsive dashboard to explore trends in repeat callers, with the ultimate goal of uncovering insights that can help the team reduce call volume, increase custoemr satisfaction, and improve operational optimization.

## Project Planning:

This project began with a stakeholder meeting to discuss the background information and goals. Using notes from the meeting, I created the following project planning documents.



These documents were instrumental in guiding the project from start to finish. 

## Data Source:

For this project, I was given access to three datasets containing call data from January thru March 2022. The data is fictionalized and anonymized and was created specifically for this case study. No licensing is required. 

The data was stored across three spreadsheets, one per market, titled the following:

```
-- Files
market_1.csv
market_2.csv
market_3.csv
```

## Data Processing:

These datasets were pre-cleaned, so very little processing was required. All that needed to be done was joining the data together into a target table to work from. After uploading the spreadsheets to BigQuery, I used the following SQL query to join the tables and prepare the data for analysis.

```
-- Join tables together
SELECT *
FROM `fiber_dataset.market_1`
UNION ALL
SELECT *
FROM `fiber_dataset.market_2`
UNION ALL
SELECT *
FROM `fiber_dataset.market_3`
```

I saved the combined results as a single table labeled `'combined_markets'` and loaded up the dataset into Tableau.

### Exploration:

The first thing I did after loading up Tableau was explore the schema to understand the data I was working with.

![Schema](https://github.com/user-attachments/assets/6ec0e6be-dc72-4ecb-b261-df6b6e903b64)

The dataset contains a record of every call received at the call center, the type of problem reported on the call, the market the call was made from, and how many repeat calls were made over the following seven day period.

### Mockup:

Using this information and everything in the project planning documents, I started work on a mock-up dashboard to serve as inspiration for the final design.

![Dashboard mockup](https://github.com/user-attachments/assets/9a03c31f-3d8b-434d-a1ac-aaa6e5722686)

I chose a number of metrics I thought might prove useful, including a high-level overview of some of the biggest KPIs that the team could track including an overall repeat call number, as well as simple statistics on calls by problem and day. Not every aspect of the mock-up survived to the final design, but having a prototype made it a lot easier to get a foothold on the project.

## Dashboard:

The mockup was a great start, but I went through several iterations of the dashboard before settling on a final design I found both clean and informative. I chose to highlight seven different metrics with varying degrees of granularity.

![tabpublic_aneSYYPBdn](https://github.com/user-attachments/assets/d36754a7-3ea5-46c7-bc52-e6fbaba895f2)
* [Interactive version](https://public.tableau.com/app/profile/tommy.demos/viz/GoogleFiber_17393798674430/GoogleFiberCallCenterAnalytics?publish=yes)

In a live environment I'm sure I would iterate further based on feedback, but for the purposes of this case study I'm quite happy with this as a finished product! It does what I set out to do: provide a snapshot of insights regarding repeat call metrics that could prove invaluable to the BI team for future analysis. 

Let me break down some of the design choices and individual charts and tables.

## Breakdown:

#### User Functionality

![filters download](https://github.com/user-attachments/assets/63a1697a-c049-4ade-8056-6e7f17811967)

First off, I wanted to make sure the entirety of the dashboard was filterable by market so the team could easily drill down and examine more localized problems. I also felt it was important to let stakeholders download a static version of the dashboard at their convenience.

---

#### Primary Metrics

As in the mockup, I curated some higher level metrics to showcase on the left side of the dashboard for easy tracking.

![tabpublic_J5S1jjYgeT](https://github.com/user-attachments/assets/74b8a945-d30e-47b0-b4cd-ba9691dfa325)

The topline number of calls and repeat calls seemed particularly important to highlight. If this were a real ongoing project, I'd also make sure to highlight how these numbers changed over time or even implementing a percentage that could easily be tracked.

![By Market](https://github.com/user-attachments/assets/fdb20b39-392b-479c-928d-a10cebd9d6c0) ![By Problem](https://github.com/user-attachments/assets/30819938-c834-468a-a52b-30f28275b4fd)

Similarly, having some very simple visualizations comparing repeat calls by market and by problem type would be critical figures to track to decide on where additional resources should be allocated. As with the topline numbers, a living dataset would include even more easily trackable KPIs with rate of change indication here as well.

Of note, the donut chart is not a native Tableau visualization, but it was something I really wanted to include. I researched some advanced techniques utilizing dummy fields and a dual axis chart and was ultimately succesful in adding it!

![Legend](https://github.com/user-attachments/assets/c9f07514-5e89-40b5-a5ef-d2e9c3b10795)

I also added my legend for the different problem types in this section, as it was needed for the donut chart as well as several other visualizations along the bottom of the completed dashboard. It made the most sense to include it here.

---

#### Drilldown Metrics

The rest of the dashboard was dedicated to some more specific data that would be useful to track over time.

![Repeat calls per Week](https://github.com/user-attachments/assets/671f9a35-1dda-4cb4-b256-8fcaed27019e)

This is a relatively simple area chart tracking the total number of calls week by week for quarter. In this case study with a limited pool of data it is static, but if this were real and changing data, the gradient would actually be dynamic. It would change color and intensity as the team made progress on their callback KPI week by week!

Despite it's visual simplictiy, it was probably the most difficult to create, as well as my favorite. Implementing a gradient effect underneath the line proved to be quite complicated and involved normalizing the data, creating a dual axis inverted chart, and mapping an image underneath. Because of the normalized data, I created an additional chart to act as the denormalized axis and made sure to use the underlying data to label each individual week as well. 

I spent more time creating this visualization than any other, but I found it a rewarding experience. I learned a lot about how powerful Tableau can be if you have a vision and commit to see it through.

![Repeat calls by Market and Problem](https://github.com/user-attachments/assets/50ccdb8f-e648-43c3-bf66-effa5036dcb6)

This is the main drilldown table for any users who want more specific figures from the primary metrics. It is color coded to the number of calls in each segment which makes it very easy to spot at a glance which problems are the biggest concern in each market. It's a relatively simple table but the impact for dashboard users could prove immense.

![Repeat calls since First Contact](https://github.com/user-attachments/assets/3c40684a-444e-4988-9140-47d8cb138b3b)

This is a fairly important metric that lets dashboard users see how soon after an initial call customers make repeat calls, further broken down by the five problem types. The visual representation should really help get a quick impression of how soon after a call the center is receiving most of their callbacks, and for what problems.

![tabpublic_wDThn4Gn8G](https://github.com/user-attachments/assets/ed3da9a5-e510-4624-85f5-2eaeebc32f98)

The final drilldown visualization I added categorizes repeat calls by the day of the week, further broken down by problem type. This chart required some additional data work using calculated columns in Tableau, but it proved worthwhile as it shows a very clear picture that the team could use to investigate further issues with customer service by day of the week.

---

## Slide Deck:

With the dashboard created, I finished up the case study by distilling much of the above analysis into an executive summary in the form of a slide deck. As the slides are meant to accompany a presentation and largely showcase much of the same information as this summary, I won't break it down as I did with the dashboard, but I've included a link for reference.

> [Slide Deck](https://docs.google.com/presentation/d/e/2PACX-1vR0tlUPoulYz_6xCt9QsoNb6Z_9U8spE5vhzvjjV8AyqZSAzNN7ZZCxyp_-kRy_nfw-LjtCLKlo6aVU/pub?start=false&loop=false&delayms=5000)

## Conclusion:

I had a lot of fun on this project. It was a lot more open ended then other case studies I've worked on and working on the design of the dashboard proved to be a great opportunity to learn more about Tableau and visualization design in general. Thanks for reading!

![bottombanner](https://github.com/user-attachments/assets/53a1271f-9d79-4814-aa4c-ea8929fe491d)



