# Phase 2 Project




### Part I: Business Understanding
King's Castles Corp is in the brainstorming phase of a new high end property development project. They are specifically interested in creating a luxurious enclosed subdivision with the express purpose of selling expensive homes.

They're new to the housing industry, just having gone bankrupt due to bad data reccomendations from a prior film start up they had invested in, and are looking to be cautious in their next investment.

They have tasked you with finding the core features that can help drive up price, and more importantly, quantifying how those features effect price.

#### Part II: Data Understanding

The data contains a range of features including square footage, bedrooms, location, a grade (based on a King County), and other variables.

Initial understanding of real estate markets will lead us to focus on square footage and location during model construction, but all other variables will be iterated through during modelling to determine any unseen relationships.

#### Part III A: Data Clean Up and Categorization

Data will undergo the following clean up process:

1. Identification of NA values, which will be converted to 0, or dropped if deemed un nescessary
2. Seperation into Catgerical and Continuous Variables
3. Run through an initial Model to determine viability of preparation

#### Part III B: Data Processing

Now that data has been segregated into its proper categories the following processing steps will take place along with modelling:

1. Categorical Data will be split into different binary columns
2. Continuous data will be normalized in order to ensure minimal heteroskedasticity
3. Target Variable will be normalized in order to ensure minimal heteroskedasticity
4. A features data set will be created in order to refer to processed data quickly later on

#### Part IV: Modelling and Adhoc Data Prep

Modelling will undergo an interative process which will involve the following steps:

1. Running an initial baseline model (worst model)
2. Feature engineering
3. Checking for Heteroskedasticity
4. Checking for Multicolinearity
5. Ensuring are R2 of 85% or higher

#### Multicolinearity Analysis Results

It appears that there are 4 pair candidates for Multicolinearity:

0	(sqft_lot_log_scaled, sqft_lot15_log_scaled)	0.918712
1	(refurbished_Refurbished More than 10 Years Ag...	0.901679
2	(sqft_living_log_scaled, sqft_above_log_scaled)	0.865059
3	(sqft_living_log_scaled, bathrooms)

In order to determine which feature to keep, a DF was created which isolated the most prominent feature.

based on this analysis the following pairs have been reccomended to be dropped:

 'sqft_lot15_log_scaled',
 'refurbished_Never Refurbished',
 'sqft_above_log_scaled',
 'bathrooms'
 
 ##### Next Actions:
 
 1. It appears that sqft_lot15 is a function of the sqft_lot and will be dropped.
 2. Refurbishing a house seems to have a binary effect on the model, wherein a refurbished house sells for more
    regardless of when it was refurbished. In order to cut down on features, a new column will be created to
    reflect that.
 3. 'sqft_above' seems to also be a function of 'sqft_living' and will be dropped
 4. Houses with larger floor plans have more bathrooms, but this doesn't mean that bathrooms is a function 
    of floor space, as such bathrooms will be kept.
 
#### Part V: Evaluation

Based on our model with an R2 of ~0.87, the following features are deemed most valuable:

1. Location
2. Grade
3. Square Footage

#### Part VI: Deployment

It is our reccomendation that the housing development be built on by a waterfront property, focus on achieving high scores on the King County grading metric, and scale their houses accordingly based on the metrics provided in our evaluation phase.