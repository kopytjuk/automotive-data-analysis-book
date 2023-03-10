# Variable types

## Overview

In the context of automotive data analysis, a variable can be thought of as a (static) characteristic or a measurement that can change or vary over time. 
Variables can be used to describe different aspects of the environment or the vehicle itself, such as its position, speed, acceleration, size, distance, object type or colour.

Variables play a crucial role in automotive data analysis because they allow us to measure and quantify the behavior of a vehicle and its surroundings. By collecting and analyzing data on these variables, we can gain insights into how an (automated) vehicle is performing, identify critical situations, evaluate the sensor performance and finally reason about its safety.

It's important to note that variables in automotive data analysis can come in different forms, such as continuous variables (e.g., speed, size or acceleration) or categorical variables (e.g., material, colour and model of the vehicle).

![var-types](./variable-types-overview.png)

## Taxonomy

### Categorical variables

**Nominal** variables are variables that have categories or labels with no inherent order or hierarchy. For example, in automotive data analysis, a nominal variable could be the make or model of a vehicle. Each vehicle belongs to a particular make and model category, but there is no inherent order or ranking between different categories. 

**Dichotomous** variables are variables that have only two possible categories or values. 
For example, in automotive data analysis, a dichotomous variable could be whether a vehicle is electric or gasoline-powered. Dichotomous variables are often analyzed using binary logistic regression, which can help identify factors that are associated with the presence or absence of a particular category or value.

**Ordinal** variables, on the other hand, have categories or labels that can be ranked or ordered based on their relative value or magnitude. 
For example, in automotive data analysis, an ordinal variable could be the level of fuel efficiency of different vehicles, which can be ranked from most fuel-efficient to least fuel-efficient. Ordinal variables are analyzed using measures such as median and quartiles, which can provide insights into the central tendency and variability of the data.

### Continuous variables

Another important type of variable in statistics is the **continuous** variable. 
Unlike nominal, ordinal, and dichotomous variables, which are categorical in nature,
continuous variables are numerical and can take any value within a range.

## Representation in Python

