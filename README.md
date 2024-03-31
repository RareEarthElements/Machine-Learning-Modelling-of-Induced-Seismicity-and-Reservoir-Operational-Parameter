# Machine-Learning-Modelling-of-Induced-Seismicity-and-Reservoir-Operational-Parameter
Machine Learning Modelling in the Geothermal Dataset

# Context
The production of geothermal steam from hydraulically/naturally fractured reservoirs is a complex process and the production rate and ultimate recovery are influenced by a number of factors. The resource potential and reservoir characteristics are predetermined by nature, drilling and completion enable the extraction of the geothermal resources, while the day-to-day operations of the operators influence the fluid dynamics and its interaction with the reservoir. In order to achieve the best possible resource recovery outcome, the drilling, completion and day-to-day operational processes must be optimised so that the designed metrics, such as best return on investment and shortest payback time or best resource recovery, can be achieved. 

A widely recognised triggering mechanism for induced earthquakes in geothermal to accommodate permeability for fluid to flow is by fluid injection, which causes pressure build-up on critically stressed faults. In addition to the injection rate, operational parameters such as wellhead pressure, total injection volume, well location, geological and geomechanical characteristics are known to have an influence on induced seismicity. 

In this study, we propose a workflow that uses a knowledge-based and data-driven approach for machine learning modelling to reveal patterns between microseismic and operational reservoir data.

# Problem Statement
Identifying the relationship between micro-earthquake (MEQ) events induced by operational reservoir parameters is very difficult using data analysis alone due to the large number of variables involved. In order to solve this problem, machine learning methods are needed to represent the pattern of characteristics of the operational reservoir parameters that have an impact on the occurrence of induced seismicity.

# Goals
The aim is to identify which reservoir operating parameters have the most significant influence on induced seismicity in this particular geothermal field. This approach is intended to help stakeholders formulate strategies for carrying out reservoir injection / stimulation and monitoring.

# Analytical Approach
We start with missing value evaluation to ensure data quality. We then checking multicollinearity and scaling all numerical features. After that, we apply machine learning modelling using different tree-based models to predict the total number of daily microseismic events. The modelling techniques only limited for tree-based models as we aim to incorporate feature importance analysis. The best selected model is the one with the lowest RMSE and MAE metrics and proceeds to model optimization using either random search or grid search hyperparameter tuning. Finally, the optimized tree-based regression model is used to represent which reservoir operating parameters of multiple injection wells are most important in inducing seismicity. 

# Metrics
The evaluation metrics to be used are RMSE and MAE

* A commonly used metric to measure the average difference between predicted and actual values is RMSE (Root Mean Squared Error). It calculates the square root of the average of the squared predicted/actual differences. The RMSE is useful because it penalises larger errors. Lower RMSE indicates better performance of models. The RMSE is used instead of the MSE to suppress values with roots due to squaring by the MSE.

* Another metric that measures the average difference between predicted and actual values is MAE (Mean Absolute Error). It calculates the absolute value of the differences between predicted and actual values and then averages these differences. It is easy to understand and interpret and is less sensitive to outliers than other metrics such as Mean Squared Error (MSE). A lower MAE is an indication of better performance of a machine learning model. The MAE measures the average error across forecasts, and the smaller the error, the closer the model's forecasts to the actuals.

# Machine Learning Method and Feature Importance Analysis
The selection of models implemented in machine learning modeling is a model that is a tree-based model to extract feature importance information in order to identify factors that influence the occurences of induced seismicity. **The trained dataset with Lasso model has the lowest average RMSE and MAE**, meaning that this model has the smallest deviation from the actual value of the target. **We then select the Lasso model for hyperparameter tuning model optimization**. However, it turns out that model optimization through hyperparameter tuning does not cause the RMSE and MAE metrics to decrease, meaning that the tuning model results are not that accurate compared to the model before tuning. 

Unexpectedly, **flow control valves in well B1 have the greatest impact on induced seismicity**, more so than the other operational reservoir parameters associated with hydraulics, like injection rate or wellhead pressure, or linked with thermals, like injection temperature. In this dataset, both injection rate and injection temperature had no effect on the generation of seismicity. However, one of the additional feature engineering of injection rate showed that **cumulative injection rate of the E1 brine well is second dominant reservoir operating parameter related to hydraulics that can be a trigger for seismicity**. In addition, it appears that wellhead pressure at wells E2 and C1 also minorly affects the occurrence of microearthquakes.

The prominence of flow control valves (FCVs) as the top-ranked feature of importance in driving induced seismicity in the machine learning model evaluation may be attributed to several factors:

**Flow Regulation**; FCVs play a critical role in regulating the flow of fluids within a reservoir or production system. Changes in fluid flow dynamics or variations in flow rates controlled by FCVs can lead to stress changes, induce changes in pressure distribution and fluid movement within the reservoir, potentially influencing the subsurface stress conditions and triggering seismic events.

**Reservoir Conditions**; The behavior of FCVs may be influenced by reservoir properties, such as reservoir pressure, fluid composition, and geological structures. Changes in these conditions can affect the operation of FCVs and, consequently, their impact on induced seismicity.

# Conclusion
**1. Machine Learning Model**
- The best machine learning model used was Lasso Model without hyperparameter tuning, with a RMSE and MAE equals 0.9% and 0.7%. 

**2. Feature Importance**
- Feature importance of the optimised lasso model showed that the seismicity rate was sensitive to the opening of the flow control valve in brine well B1 that might be governed wheter by flow regulation or resevoir condition, and the cumulative injection rate in brine well E1.
- However, as injectivity is dependent on the temperature of the injected water in all wells, the implementation of machine learning modelling for this geothermal dataset does not demonstrate that thermal effects drive induced seismicity.
