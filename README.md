# Supply-Chain-Analysis-for-Retail
This project presents a comprehensive inventory optimization strategy using predictive analytics with historical sales data. It demonstrates that the value of data-driven forecasting lies not only in predicting demand, but also in translating those predictions into actionable inventory decisions to improve stock planning and reduce uncertainty.


# IS525E – Data Science for Business

# Supply Chain Analytics

Inventory Optimization Using Predictive Analytics

Dataset: apple_global_sales_dataset.csv

# Team members: YU-HSIN LIU, Fernanda AGUIRRE OROPEZA, René Alfonso SORIANO RUIZ

# Project overview

This project uses Apple global sales data to answer a practical supply chain question: how much stock should the company prepare next month for the most important products inside each category?

To make the analysis more useful from a business perspective, we do not stay with one global ranking. Instead, we keep the top 3 products within each category based on total units sold. That gives a more balanced view across iPhone, Mac, iPad, Apple Watch, AirPods, and Accessories.

The project keeps a monthly planning perspective. It studies recent sales behavior, compares three predictive models, selects the strongest option, and then translates the forecast into operational metrics such as safety stock, reorder point, target stock level, and recommended order quantity.

# The project outlines:

Define the problem
Clean the data
Explore demand patterns
Build and evaluate the models
Create the inventory plan


# 1. PROBLEM STATEMENT AND OBJECTIVE

Inventory decisions matter because both extremes are costly. When stock is too low, the company risks losing sales and affecting the customer experience. When stock is too high, working capital remains tied up in products that are not moving fast enough.

The central business question is straightforward:

How can historical sales data help improve inventory planning for the most important products inside each category?

The objective is to build a forecasting workflow that estimates next-month demand and turns that estimate into a practical inventory plan. In other words, the purpose is not only to describe what happened in the past. The purpose is to support a better operational decision for the next planning cycle.

# 2. JUSTIFICATION

A supervised regression approach makes sense because the decision depends on estimating future demand. Monthly sales usually contain signals from recent history, and those signals can be converted into more informed replenishment decisions.

The notebook compares three models with different strengths. Linear Regression works as a clear and interpretable baseline. Random Forest helps when the relationship is less linear. Gradient Boosting provides another strong benchmark when interactions matter more.

The models are evaluated with MAE, RMSE, MAPE, and R². Together, these metrics help answer a practical question: which model is accurate enough to support inventory planning in a realistic way?

# 3. INITIAL DATA EXPLORATION

At this stage, the goal is simply to confirm that the dataset is usable for the business question. A quick inspection helps verify the structure, identify possible missing values, and highlight the fields that matter most for inventory planning.

For this project, the key variable is units_sold, because it represents demand. The date field is also essential, since the analysis will later be organized at the monthly level.

# 4. CHECK MISSING VALUES AND DUPLICATES

We convert the date field, keep the rows that are valid for this analysis, and remove duplicates if they exist.

Some variables contain missing values, but not all of them are critical for this supply chain problem. Since the objective is demand forecasting and inventory planning, we keep the preparation focused on the variables that directly support that decision.

# 5. CLEAN THE DATA

Since we found missing values only on the columns that have categorical information that is not relevant to the study, we only removed duplicated rows and droped the unused columns.

# 6. BASIC DESCRIPTIVE ANALYSIS
At this point, the goal is to identify where inventory decisions matter most. The category view shows where the largest share of demand is concentrated, while the product view gives a first signal of which items are strongest overall.

This makes the next selection rule easier to justify. Instead of keeping only one overall ranking, the project retains the top 3 products within each category so the analysis stays broad, balanced, and relevant across the portfolio.

These charts show that demand is not distributed evenly across the portfolio. That matters because inventory planning should not treat all products in the same way.

By keeping the top 3 products within each category, the project avoids overconcentrating the analysis in a single product family and creates a more useful business view of where replenishment priorities may emerge.

# 7. SELECT THE TOP 3 PRODUCTS IN EACH CATEGORY

Instead of working with individual transactions, we reorganize the information at the monthly level. This is more useful because procurement and replenishment are usually reviewed by period, not by single sale.

At the same time, we keep the color signal in the data by creating color dummies before monthly aggregation. That way, the monthly dataset stays simple enough for modeling while still preserving information that can later support product-color recommendations in the inventory plan.
For product selection, we choose the top 3 products inside each category based on total units sold.

When the monthly dataset is built, color is encoded before aggregation. This preserves the variation associated with color without turning the full analytical table into a much more fragmented time series. That is a practical middle ground due to the model learns from monthly demand patterns, and the final recommendation can still reconnect the analysis with product-color decisions.


# 8. ENCODE THE VARIABLE 'color'
We were assuming that Color might affect how much a product sells. Encoding the color variable enabled the model to incorporate product-level attributes into demand forecasting, allowing for a more detailed and realistic representation of customer preferences.

# 9. BUILD A MONTHLY PRODUCT-COLOR LEVEL DATASET

The dataset was structured at a product-color-month level to capture demand patterns over time at a granular level. By aggregating the data at a monthly product-color level, the analysis captures both temporal dynamics and product variation, enabling more accurate demand forecasting and more targeted inventory strategies.

# 10. VISUALIZE MONTHLY DEMAND FOR THE SELECTED PRODUCTS
The monthly demand lines show clearly that demand is not constant. Some products move in a steadier way, while others fluctuate much more from month to month.

That is exactly why predictive analytics is useful here. A fixed replenishment rule would likely ignore those differences, while a data-driven approach can adapt more intelligently to recent sales behavior.

# 11. FEATURE ENGINEERING FOR PREDICTIVE ANALYTICS 

Predictive analytics becomes more useful when the dataset captures recent demand behavior. We create lag variables, rolling averages, rolling standard deviations, and calendar variables. These features help summarize what has been happening recently and give the model a better basis for estimating future demand and uncertainty.

The only categorical information included in the model is **color** through dummy variables. The rest of the predictive inputs are numerical.
These features help the model answer practical questions such as what happened last month, whether demand has been trending up or down, and how volatile recent sales have been. That matters because inventory planning is not only about average demand, it is also about uncertainty and stability.

# 12. SPLIT THE DATA INTO TRAIN AND TEST

Because this is a supply chain problem with a time dimension, chronology should be respected. Past and future observations should not be mixed randomly. For that reason, the we train with earlier months and reserves the most recent period (Q4 2024) for testing.

A time-based split is important because, in a real business setting, future demand is always predicted using past information. This makes the test more credible and helps show whether the model can support decisions under realistic conditions.

# 13. SCALE THE FEATURES
Feature scaling ensures that all variables are treated with equal importance during model training by standardizing feature values.

# 14. TRAIN THE THREE MODELS

Three models are compared because demand can behave in different ways. Some patterns may be closer to a linear trend, while others may depend on nonlinear effects or interactions among variables.

Comparing the models avoids choosing a method by assumption. Instead, the we let the evidence from the holdout period guide the decision.
MAE shows the average absolute error in units. RMSE penalizes larger misses more heavily. MAPE expresses the error as a percentage, which is usually easier to explain to a business audience. R² provides a general sense of how much of the demand pattern the model is capturing.

For inventory planning, RMSE and MAPE are especially useful because weak demand estimates translate directly into weaker reorder decisions.


# 15. MODEL SELECTION
The selected model is the one that provides the most reliable balance across the evaluation metrics.

The goal is not to find a perfect forecast, is to find a model that is accurate enough to support better replenishment decisions than a simple rule of thumb.

# 16. FORECAST

A perfect forecast is not realistic in supply chain work. What matters is whether the model is strong enough to support better decisions than a simple guess or a fixed rule. In this project, the selected model creates a practical bridge between demand estimation and inventory planning.

After selecting the best model, we estimate next-month demand and converts those estimates into inventory indicators. In the final planning stage, the analysis reconnects the monthly model output with category, product, and color, so the recommendation becomes easier to use operationally.

# 17. INVENTORY OPTIMIZATION
This graph presents a full inventory plan based on the historical data of the last 6 months fro the top 3 products of each cathegory. It includes the number of predicted units for next month, the lead time, safety stock, reorder points, target stock level and the recommended order quantity.

# 18. ABC ANALYSIS
The ABC analysis is a Supply Chain Management tool that divides inventory in 3 classes based on the cost of volume in inventory where:

A: Highest cost (<60% of cumulated cost)

B: Medium cost

C: Lower cost (>80% of cumulated cost)

This It helps to establish policies that focus on the few critical parts and not on the most trivial ones, in this case, the top 3 products for each category.

# 19. REORDER POINTS
It is necessary to know the exact dates of reordering products according to the date when the stock reaches the marked level. This is to avoid both stockouts and overstock. We decided to perform the reorder point analysis in the predicted demand, but basing on the historical demand.

# 20. SAFETY STOCK LEVELS
Safety stock buffer is what makes the reorder point realistic instead of risky. It helps to be aware of how many products are in stock in order to protect against uncertainty. Since Apple launches new products every year, the stock buffer is every time lower for the products that are moving everytime more aside in order for the new products to enter, which is why the olderst generations of products are the lowest.

# 21. EXECUTIVE INVENTORY PLAN

This table shows a summary of the ABC analysis, the reorder points and the safety stock, as well as many other important information for a supply chain manager to understand what happens with the products and be aware of the next steps

# 22. APPLE INVENTORY OPTIMIZATION DASHBOARD

Rather than adding more technical detail, it highlights the main decisions: where forecast demand is concentrated, which categories require the largest replenishment effort, which product-color combinations deserve closer attention, and how the selected model performed.

# 23. FINAL CONCLUSION

It is undeniable that for Apple, as for any company, demand is volatile, especially for an innovative and well-established one. In this project, we presented a comprehensive supply chain analysis, relying not only on the analysis of historical sales data and the construction of predictive models, but also on a rigorous framework. This allowed us to estimate future demand trends for flagship products and evaluate the model's performance using error metrics such as mean absolute error (MAE) and root mean square error (RMSE). To do this, we selected the three best-performing products in each category offered by Apple, focusing on the most important products for the coming year, which enabled a more strategic and business-oriented analysis.

It is important to note that Apple launches new products in almost all of its categories every year. Therefore, even if demand appears stable throughout the year, it experiences significant fluctuations at certain times. This is why supply chain managers need to closely monitor their inventory levels.

This study demonstrates how predictive analytics can significantly improve inventory management by shifting from reactive to data-driven decision-making. The results showed that demand varies not only over time but also from product to product, highlighting the importance of segmenting inventory decisions rather than applying a one-size-fits-all approach.
Furthermore, by incorporating forecast errors into safety stock calculations, the study introduced a dynamic margin that adapts to uncertainty. This approach improves service levels while reducing the risk of overstocking, thus providing a more efficient balance between availability and cost.

Overall, integrating demand forecasting, product-level analytics, and inventory optimization concepts (such as reorder point and safety stock) provides a scalable framework for improving supply chain performance.

Future improvements could include the use of more advanced forecasting models, the integration of external variables (such as promotions or seasonal factors) and the simulation of inventory management policies to further optimize ordering strategies.
