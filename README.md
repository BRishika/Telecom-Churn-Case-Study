# Telecom-Churn-Case-Study

Telecom Churn Case Study

Business Problem Overview
Customers in the telecom industry are able to choose from a variety of service providers and actively switch between operators. The telecom business typically experiences an annual turnover rate ranging from 15% to 25% in this extremely competitive market. The emphasis has switched to prioritising customer retention over customer acquisition due to the fact that obtaining a new customer can cost 5 to 10 times more than keeping an existing one.
Retaining highly profitable customers is the primary business goal for many established telecom carriers.
Telecom businesses must proactively identify those customers who are at a higher risk of leaving in order to prevent customer churn.
In this project, we will examine customer-level data from a well-known telecom company, build prediction models to identify customers who are likely to leave, and identify the major factors that influence churn.

Understanding and Defining Churn
The two main payment models used by the telecom sector are post-paid and prepaid. With post-paid, clients pay a monthly or annual bill after using services, and with prepaid, they pay or recharge an amount in advance and use services later.
In the post-paid model, users often inform their existing provider to discontinue services when they decide to switch to a different operator, making churn detection simple.
Customers who want to migrate to another network can halt service usage immediately under the prepaid model, in contrast. Due to this circumstance, it can be difficult to tell if someone has truly churned or is merely abstaining from using services for a while (for instance, when taking a protracted trip abroad with the intention of returning to them later).
As a result, churn prediction is frequently more important and difficult for prepaid consumers, calling for a clear definition of the term "churn." It's also important to remember that postpaid is more common in Europe and North America, whereas prepaid is more common in India and Southeast Asia.
The Indian and Southeast Asian telecommunications markets are the main focus of this project.

There exist several methods to define churn, including:

1.	Revenue-based churn: Identifying customers who have not engaged in revenue-generating activities, such as mobile internet, outgoing calls, SMS, etc., within a specified timeframe. Alternatively, one can employ aggregate metrics, like 'customers who have generated less than INR 4 per month in total/average/median revenue.' 
The primary limitation of this definition lies in the fact that it doesn't account for customers who solely receive calls/SMS from wage-earning family members, thereby not generating revenue themselves. For instance, many rural users solely receive calls from their urban-based wage-earning siblings.

2.	Usage-based churn: Identifying customers who have exhibited zero usage, be it incoming or outgoing, across various services like calls, internet, etc., during a specific period.
A potential drawback of this definition is that it may be too late to take corrective actions to retain customers once they have stopped using the services for an extended period. For example, if churn is defined based on a 'two-months zero usage' criterion, predicting churn may become impractical, as the customer may have already switched to another operator by that time.
In this project, we will adopt the **usage-based** definition to delineate churn.

High-Value Customer Churn Analysis
In the context of the Indian and Southeast Asian telecom market, it's crucial to recognize that approximately 80% of the revenue originates from the top 20% of customers, known as high-value customers. Therefore, addressing churn among these high-value customers becomes paramount in reducing substantial revenue loss.
Within this project, we will delineate high-value customers based on a specific metric (detailed later) and focus our churn prediction efforts exclusively on this segment.

Understanding the Business Objective and Dataset
The dataset encompasses customer-level data spanning four consecutive months, denoted as June (6), July (7), August (8), and September (9). The core objective is to predict customer churn in the ninth month (i.e., September) by leveraging data from the preceding three months. To achieve this goal effectively, gaining insights into typical customer behaviour during churn is essential.

Analysing Customer Behaviour During Churn
Customers typically do not make an instantaneous decision to switch to a different provider but rather transition over a period. This especially holds true for high-value customers. In the context of churn prediction, we consider three phases in the customer lifecycle:
The 'Good' Phase: During this phase, customers are content with the service and exhibit regular behaviour.
The 'Action' Phase: The customer experience deteriorates during this phase due to various factors, such as receiving enticing offers from competitors, encountering unjust charges, or experiencing declining service quality. Customers often demonstrate different behaviour patterns compared to the 'good' months. Identifying high-churn-risk customers in this phase is crucial, as it presents an opportunity for corrective actions, like matching competitor offers or improving service quality.

The 'Churn' Phase: In this phase, customers are considered to have churned. Our churn definition is based on this phase. Importantly, at the time of prediction (i.e., during the 'action' months), data from the 'churn' phase is not yet available for forecasting. Therefore, after tagging churn as 1/0 based on this phase, all data pertaining to this phase is discarded.
For this project's four-month window, the first two months constitute the 'good' phase, the third month represents the 'action' phase, and the fourth month is the 'churn' phase.

Dataset and Data Dictionary
A data dictionary is provided, offering explanations for abbreviations used. Common abbreviations include "loc" (local), "IC" (incoming), "OG" (outgoing), "T2T" (telecom operator to telecom operator), "T2O" (telecom operator to another operator), "RECH" (recharge), etc. Attributes with '6', '7', '8', '9' as suffixes indicate data for the respective months.

Data Preparation
Effective data preparation is crucial and includes the following steps:
1.	Feature Engineering: Deriving new features based on business understanding to identify potential indicators of churn.
2.	High-Value Customer Selection: Defining high-value customers as those who recharge with an amount greater than or equal to the 70th percentile of average recharge amounts in the first two months (the 'good' phase).
3.	Churn Tagging and Data Removal: Identifying churned customers (churn=1) based on the fourth month, where they have not made any calls (incoming or outgoing) and have not used mobile internet even once during the 'churn' phase. Attributes with '_9' suffixes are removed, corresponding to the 'churn' phase.

Modelling
Our modelling efforts serve two primary purposes:
1.	Churn Prediction: Develop predictive models to determine whether high-value customers will churn during the near future (i.e., the 'churn' phase). This knowledge enables the company to take proactive measures such as offering special plans or recharge discounts.
2.	Feature Importance: Identify key predictor attributes that strongly influence churn. These variables may shed light on why customers opt to switch to other networks.
Given the large number of attributes, dimensionality reduction techniques like PCA will be employed before building predictive models. Additionally, techniques for handling class imbalance will be applied since churn rates are typically low (around 5-10%).


Our modelling approach entails:

1.	Data pre-processing (format conversion, handling missing values, etc.).
2.	Exploratory analysis to extract valuable insights.
3.	Feature engineering.
4.	Dimensionality reduction using PCA.
5.	Model training, hyper parameter tuning, and addressing class imbalance.
6.	Model evaluation using appropriate metrics prioritizing churner identification.
7.	Model selection based on evaluation metrics.
To achieve the second goal of identifying significant predictor attributes, a separate model, such as logistic regression or a tree-based model, will be employed, with attention to addressing multi-collinearity. Visual representations, such as plots and summary tables, will be used to showcase feature importance.
Ultimately, recommendations for managing customer churn will be based on our observations and findings.


**Files uploaded:**
1. README file: README.md
2. Python notebook: telecom churn case study.ipynb
3. Case study pdf: Telecom Churn Case Study.pdf
4. Excel file: telecom_churn_data.csv
