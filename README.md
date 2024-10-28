# CEO-Request-Project
CEO-Request Challenge
1. Summary of Problem Statement
❓ How could Olist improve its profit ❓

P&L Rules
Revenues
Sales fees: Olist takes a 10% cut on the product price (excl. freight) of each order delivered
Subscription fees: Olist charges 80 BRL by month per seller

Costs
Reputation costs estimated per order with bad reviews (<= 3 stars)

💡 In the long term, bad customer experience has business implications: low repeat rate, immediate customer support cost, refunds or unfavorable word of mouth communication. We will assume that we have an estimate measure of the monetary cost for each bad review:

# review_score: cost(BRL)
{'1 star': 100
'2 stars': 50
'3 stars': 40
'4 stars': 0
'5 stars': 0}
IT costs: Olist's total cumulated IT Costs scale with the square root of the total number of sellers that has ever join the platform, as well as the square root of the total cumulated number of items that were ever sold.


Olist's data team gave us the following values for these scaling parameters:

💡 Both number of sellers to manage and sales transaction are costly for IT systems.
💡 Yet square roots reflect scale-effects: IT-system are often more efficient as they grow bigger.
💡 Alpha > Beta means that Olist has a lower IT Cost with few sellers selling a lot of items rather than the opposite

with 1000 sellers and a total of 100 items sold, the total IT cost accumulates to 109,624 BRL
with 100 sellers and a total of 1000 items sold, the total IT cost accumulates to 62,507 BRL
Finally, The IT department also told you that since the birth of the marketplace, cumulated IT costs have amounted to 500,000 BRL.

Key Findings, so far
wait_time is the most significant factor behind low review scores
wait_time is made up of seller's delay_to_carrier + carrier_delivery_time.
The latter being outside of Olist's direct control, improving it is not a quick-win recommendation
On the contrary, a better selection of sellers can positively impact the delay_to_carrier and reduce the number of bad review_scores on Olist.
Comments of the bad reviews showed that some were linked to the seller or to the product itself.
💡 We recommend you to start with the the guided seller analysis in part 2 below
💪 But feel free to investigate into other hypothesis instead with part 3

2. Should Olist remove under-performing sellers from its marketplace? 🕵🏻
(recommended)

To analyze the impact of removing the worse sellers from Olist's marketplace, we will perform a what-if analysis

👉 What would have happened if Olist had never accepted these sellers in the first place?

(In practice, it's hard to know in advance who is a good seller, but let's start with this approach and iterate later).

2.1 Data Preparation
Compute, for each seller_id, and cumulated since the beginning:

the revenues it brings
the review_costs associated with all its bad reviews
the resulting profits (revenues - costs)
👉 Write down a step-by-step strategy to create the DataFrame you need

⚠️ Don't start from scratch, update your existing package 😉

Starting from the Seller class of your olist package:

Edit the get_training_data method so that the DataFrame it returns contains the fields:

revenues: sum of subscription and sales fees revenues
cost_of_reviews: sum of costs associated with bad reviews
profits: revenues - cost_of_reviews
2.2 What-if Analysis
👉 Time to perform the actual analysis, here are our steps:

1️⃣ Create a method that will help us update the IT Costs after removing sellers along with the items they sold

2️⃣ Sort sellers by increasing profits

3️⃣ Remove sellers one by one, starting from the one with the lowest profit.

For each number of sellers to remove, compute the financial impact on Olist global profits.
4️⃣ Find an optimal number of sellers to remove that maximizes either Olist's profit margin or profit.

3. Investigate other Approaches 🕵️
(optional)

Should Olist remove the worst performing products / categories from its marketplace entirely?
