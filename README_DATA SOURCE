About Dataset
🍎 Apple Global Product Sales Dataset

11,500 synthetic sales transactions for iPhone, iPad, Mac, Apple Watch, AirPods, and Accessories
across 47 countries, 514+ cities, sorted by Country → City → Date (2022 – 2024).
📌 About This Dataset

This dataset simulates a realistic global sales ledger for Apple Inc. products.It covers city-level transactions across multiple continents, currencies, sales channels,and customer demographics — ideal for retail analytics, market segmentation, price analysis, time-series forecasting, and geographic visualisation.

⚠️ All figures are synthetically generated for educational / portfolio purposes.
They do not represent actual Apple Inc. financial data.
📁 File

File	Rows	Columns	Size
apple_global_sales_dataset.csv	11,500	27	~2.9 MB
📋 Column Dictionary

#	Column	Type	Description
1	sale_id	string	Unique transaction ID —APPL-XXXXXXXX
2	sale_date	date	Transaction date YYYY-MM-DD
3	year	int	2022 / 2023 / 2024
4	quarter	string	Q1 / Q2 / Q3 / Q4
5	month	string	Full month name
6	country	string	Country of sale
7	region	string	Continent / geo-region
8	city	string	City of sale
9	product_name	string	Full product name
10	category	string	iPhone / iPad / Mac / Apple Watch / AirPods / Accessories
11	storage	string	Storage variant (N/A for non-storage products)
12	color	string	Colour option
13	unit_price_usd	float	Per-unit list price in USD (±8 % market jitter)
14	discount_pct	float	Discount applied: 0, 2, 3, 5, 7, 10, or 15 %
15	units_sold	int	Quantity in this transaction (1–8, skewed toward 1)
16	discounted_price_usd	float	Effective per-unit price after discount
17	revenue_usd	float	Total transaction revenue in USD
18	currency	string	Local currency code
19	fx_rate_to_usd	float	Exchange rate used for conversion
20	revenue_local_currency	float	Revenue in local currency
21	sales_channel	string	Apple Store / Online / Reseller / Carrier / Retailer / B2B
22	payment_method	string	Credit Card / Debit Card / Apple Pay / EMI / Net Banking / Cash / Gift Card
23	customer_segment	string	Individual / Business / Education / Government
24	customer_age_group	string	18–24 / 25–34 / 35–44 / 45–54 / 55+
25	previous_device_os	string	Previous OS (iPhone buyers only; others →N/A)
26	customer_rating	float	Post-purchase rating 3.0–5.0; ~30 % are NaN
27	return_status	string	Kept / Returned / Exchanged
🌍 Countries Covered (47)

Region	Countries
North America	United States, Canada, Mexico
South America	Brazil, Argentina, Chile, Colombia
Europe	United Kingdom, Germany, France, Italy, Spain, Netherlands, Poland, Sweden, Switzerland, Norway, Denmark, Finland, Portugal, Austria, Belgium, Ireland, Turkey, Russia
Asia	India, China, Japan, South Korea, Indonesia, Pakistan, Singapore, Malaysia, Thailand, Vietnam, Philippines, Taiwan, Hong Kong, Bangladesh
Middle East	Saudi Arabia, UAE, Egypt
Africa	South Africa, Nigeria, Kenya
Oceania	Australia, New Zealand
📦 Products Covered (43)

Category	Models
iPhone (13)	SE 3rd Gen · 13 Mini · 13 · 13 Pro · 13 Pro Max · 14 · 14 Plus · 14 Pro · 14 Pro Max · 15 · 15 Plus · 15 Pro · 15 Pro Max
iPad (5)	iPad Mini 6 · iPad 10th Gen · iPad Air M1 · iPad Pro 11" M2 · iPad Pro 12.9" M2
Mac (7)	MacBook Air 13" M2 · MacBook Air 15" M2 · MacBook Pro 14" M3 · MacBook Pro 16" M3 Pro · Mac mini M2 · Mac Pro M2 Ultra · iMac 24" M3
Apple Watch (4)	SE 2nd Gen · Series 8 · Series 9 · Ultra 2
AirPods (4)	AirPods 2nd Gen · AirPods 3rd Gen · AirPods Pro 2nd Gen · AirPods Max
Accessories (10)	Apple TV 4K · HomePod · HomePod mini · Magic Keyboard · Magic Mouse · Magic Trackpad · Apple Pencil 1st Gen · Apple Pencil 2nd Gen · MagSafe Charger · USB-C Cable
📊 Row Distribution

Category	Rows
iPhone	~3 444
Accessories	~2 615
Mac	~1 873
iPad	~1 379
Apple Watch	~1 126
AirPods	~1 063
Total	11 500
💡 Suggested Analyses

Revenue by Country / City — Which markets drive iPhone revenue the most?
Category Mix by Region — iPhone dominance in Asia vs Mac in Europe
Channel Performance — Apple Store vs Online vs Resellers by country
Discount Impact — Does discounting drive higher volumes and revenue?
Seasonality (Q4 surge) — Holiday effect across product lines and regions
Currency Analysis — Revenue comparison normalised to USD
Customer Segmentation — Individual vs Business vs Education buyers
Return Rate — Which product/country combos have highest returns?
OS Switching — What % of iPhone buyers switched from Android?
Age Group Preferences — Which demographics favour which product categories?
🛠️ Generation Details

Script: generate_apple_sales.py (Python 3, no external deps)
Seed: 42 — results are fully reproducible
Sort: Country → City → Date (ascending)
Prices: Based on real Apple 2022–2024 pricing with ±8 % market jitter
FX Rates: Representative 2023 midpoint rates
Missing data: customer_rating is NaN for ~30 % rows (realistic survey drop-off)
Return status weights: Kept 88 % · Returned 8 % · Exchanged 4 %



# DOI (DIGITAL OBJECT IDENTIFIER)

# Released under MIT License

Copyright (c) 2013 Mark Otto.

Copyright (c) 2017 Andrew Fong.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
