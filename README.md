
##  Aviation Risk Analysis for Aircraft Investment  

###  Introduction  
This analysis explores aviation accident data to provide insights into the **best aircraft models** for investment, aiming to **minimize risks and operational costs** for the company.  

To uncover the safest and most cost-effective aircraft, we conducted a detailed assessment based on the following key objectives:  

###  Key Analysis Areas  
- **Accident Rate by Aircraft Make & Model** – Identifying aircraft with the lowest accident occurrences. 

- **Severity Analysis** – Evaluating the level of risk (fatal vs. minor accidents) associated with different aircraft. 

- **Causes of Accidents** – Distinguishing between human-related and mechanical failures.  

- **Purpose of Flight & Risk** – Comparing accident trends between **commercial and private aircraft**. 

- **Geographic Risk Factors** – Analyzing accident-prone locations and weather-related risks. 


These insights will guide the company's **aviation investment strategy**, ensuring informed decision-making when purchasing aircraft for commercial and private use.  
# Data source and structures 
## Data Exploration  

The dataset used in this analysis is sourced from the **NTSB Aviation Accident Database**, which records civil aviation accidents and selected incidents occurring in the **United States and international waters** from **1962 to 2023**. The dataset consists of **two tables** and was obtained from **Kaggle**.  

 **Dataset Link:** [Aviation Accident Database](https://www.kaggle.com/datasets/khsamaha/aviation-accident-database-synopses)  

### Dataset Overview  
### Dataset Overview  
The dataset contains **88,889 records** with **31 columns**, capturing various details of aviation accidents. To determine the data types of each column, the following code was executed:  

```python
df.dtypes
```
The columns were as follows 
| Column Name                 | Data Type | Description                               |
|-----------------------------|-----------|-------------------------------------------|
| Event.Id                    | Object    | Unique identifier for each event         |
| Investigation.Type          | Object    | Type of investigation (Accident or Incident) |
| Accident.Number             | Object    | Reference number assigned to the accident |
| Event.Date                  | Object    | Date of the event                        |
| Location                    | Object    | City or area where the event occurred    |
| Country                     | Object    | Country where the event took place       |
| Latitude                    | Object    | Latitude coordinates of the event        |
| Longitude                   | Object    | Longitude coordinates of the event       |
| Airport.Code                | Object    | Airport code if applicable               |
| Airport.Name                | Object    | Name of the airport where the event occurred |
| Injury.Severity             | Object    | Severity level of injuries               |
| Aircraft.Damage             | Object    | Extent of damage to the aircraft         |
| Aircraft.Category           | Object    | Category of the aircraft involved        |
| Registration.Number         | Object    | Registration number of the aircraft      |
| Make                        | Object    | Manufacturer of the aircraft             |
| Model                       | Object    | Specific model of the aircraft           |
| Amateur.Built               | Object    | Indicates if the aircraft was amateur-built |
| Number.of.Engines           | Float     | Number of engines on the aircraft        |
| Engine.Type                 | Object    | Type of engine installed in the aircraft |
| FAR.Description             | Object    | Federal Aviation Regulations category    |
| Schedule                    | Object    | Schedule type (e.g., commercial, private) |
| Purpose.of.Flight           | Object    | Intended purpose of the flight           |
| Air.Carrier                 | Object    | Name of the airline or carrier           |
| Total.Fatal.Injuries        | Float     | Number of fatal injuries                 |
| Total.Serious.Injuries      | Float     | Number of serious injuries               |
| Total.Minor.Injuries        | Float     | Number of minor injuries                 |
| Total.Uninjured             | Float     | Number of uninjured individuals          |
| Weather.Condition           | Object    | Weather conditions during the event      |
| Broad.Phase.of.Flight       | Object    | Phase of flight during the event        |
| Report.Status               | Object    | Status of the investigation report       |
| Publication.Date            | Object    | Date the report was published            |
# Data Cleaning & Preparation
Data was loaded using pandas also other libraries such as matplotlib ,seaborn and numpy were imported,The code below shows how the libraries were imported and also how the aviation data was loaded for cleaning and analysis
```python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv("data/aviation_data.csv")

# Display first few rows
df.head()
```


To ensure data consistency and improve the quality of insights, the dataset underwent several cleaning and preprocessing steps.

 **Identifying Data Types**

The dataset was divided into numerical and categorical columns to facilitate appropriate handling.

**Numerical Columns included**:

Number.of.Engines, Total.Fatal.Injuries, Total.Serious.Injuries, Total.Minor.Injuries, Total.Uninjured, Latitude, Longitude

**Categorical Columns included**:

Event.Id, Investigation.Type, Accident.Number, Event.Date, Location, Country, Airport.Code, Airport.Name, Injury.Severity, Aircraft.Damage, Aircraft.Category, Registration.Number, Make, Model, Amateur.Built, Engine.Type, FAR.Description, Schedule, Purpose.of.Flight, Air.Carrier, Weather.Condition, Broad.Phase.of.Flight, Report.Status, Publication.Date

**Numerical Data cleaning 

 *Misiing values

Missing values were filled using the median to prevent skewing the dataset.

 *Outlier Removal

The IQR (Interquartile Range) method was applied to detect and remove outliers from numerical columns. This ensures that extreme values do not distort the overall analysis.

 **Categorical Data Cleaning

-All text data was converted to lowercase for uniformity.

-Categorical Columns: Missing values were replaced with "unknown" to retain relevant records and prevent data loss.

-Irrelevant columns such as Event.Id, Accident.Number, Publication.Date, Amateur.Built,schedule,Air carrier were dropped.

-Latitude and Longitude were converted to numeric values, and missing values were filled with 0 to maintain data integrity.

-Categorical columns were converted to the category data type to optimize memory usage and improve processing efficiency.

-The categorical and numerical columns were combined using the concatenation method for further analysis.

**The cleaned data was saved and can be viewed through this link https://github.com/DEE-arch-blip/Phase1-Project-/blob/4c1ec305fc0bd318084136a6c8876d394b9ea342/project.ipynb/cleaned_data.csv

 ## Data Analysis & Visualizations  
We analyzed accident trends, severity distribution, Accident prone locations and  major accident causes.  
Key visualizations include:  
- Accident trends over time  
- Severity distribution by aircraft type  
**The analysis and visualizations can be viewed here https://github.com/DEE-arch-blip/Phase1-Project-/tree/master/project.ipynb
# key findings 
1. **Most Accident-Prone Aircraft Makes and Models:**
   - **Cessna (27,149 accidents), Piper (14,870 accidents), and Beech (5,372 accidents)** account for the highest number of accidents.
   - The **Cessna 152, 172, and 172N models** are the most accident-prone, with accident counts of 2,367, 1,756, and 1,164, respectively.
   - These aircraft are widely used for personal, instructional, and general aviation, which may contribute to the high accident rates.

2. **Flight Purpose and Accident Trends:**
   - **Personal flights (49,448 accidents)** dominate accident occurrences, followed by **unknown (12,994) and instructional flights (10,601).**
   - Business flights and aerial applications also contribute significantly to the total accident count.
   - Low-accident categories include air races, firefighting, and glider towing, likely due to strict regulations and limited flight frequency.

3. **Geographic and Airport-Based Insights:**
   - **Anchorage, AK (548 accidents), Miami, FL (275), and Houston, TX (271)** have the highest accident occurrences.
   - **Unknown airports and private airstrips** report the most accidents, indicating possible gaps in safety infrastructure and air traffic control at smaller airports.

4. **Engine Type and Accident Distribution:**
   - **Reciprocating engines (69,530 accidents)** are linked to the most accidents, likely due to their widespread use in small aircraft.
   - **Turbojet and electric-powered aircraft have relatively low accident counts**, suggesting that modern propulsion systems may have better safety performance.

5. **Broad Phase of Flight and Accidents:**
   - The **highest number of accidents occur during landing (15,428), takeoff (12,493), and cruise (10,269).**
   - These phases are critical in flight safety and require improved monitoring and pilot training.

6. **Historical Trends:**
   - The highest accident rates were recorded between **1982 and 2000**, with a peak in 1982 (3,593 accidents).
   - A **steady decline in accidents post-2000** suggests improvements in aviation safety standards, technology, and pilot training.

---
# Dasboards Visualization 
![Visualization: Aircraft accident rates by make,model and injury severity] (https://github.com/DEE-arch-blip/Phase1-Project-/blob/master/images/Tablue%20Dashboard.png) 

![Visualization:purpose of flight and accident location] (https://github.com/DEE-arch-blip/Phase1-Project-/blob/master/images/tablue%20dasboard2.png)
![Visualization, number of engine, trends and broad phase ] (https://github.com/DEE-arch-blip/Phase1-Project-/blob/master/images/tablue%20dashboard%203.png)



# Recomendations
1. **Choosing the Right Aircraft Fleet:**
   - Avoid aircraft models with **historically high accident rates** unless additional safety measures are implemented.
   - Consider modern aircraft with **better safety records** and advanced avionics.
   - If using **Cessna or Piper aircraft**, implement **rigorous maintenance and pilot training programs**.

2. **Focusing on a Safe Business Model:**
   - If setting up a **flight training school**, prioritize **aircraft with high safety ratings** and enforce strict instructor-to-student supervision.
   - For **air charter services**, use aircraft equipped with **advanced safety features** like AI-assisted navigation and real-time tracking.
   - Aerial application (crop dusting) businesses should focus on **pilot training** and **weather monitoring systems** to minimize risks.

3. **Selecting a Safe Location & Infrastructure:**
   - If operating from a **private airstrip**, invest in **runway lighting, weather monitoring, and communication systems** to reduce accident risks.
   - Setting up near **controlled airports with ATC supervision** improves safety and reduces mid-air collisions.
   - Avoid locations with **historically high accident rates**, unless safety improvements are in place.

4. **Implementing High Safety Standards:**
   - Regularly inspect and maintain aircraft, focusing on **reciprocating engine safety checks**.
   - Use **predictive maintenance technology** to detect engine issues before failures occur.
   - Provide **annual safety training for pilots and ground crew** to reinforce emergency protocols.



