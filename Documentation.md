These instructions follow https://github.com/mHienp/GCBM.EmeraldEdge.Data/wiki/Documentation

# Documentation on How to Run A GCBM Model

## Step 1: Determine Administrative and Forest Boundaries

To determine administrative and forest boundaries, follow these steps:

1. Access the [Land Sector Datasets](https://datasets.mojaglobal.workers.dev/0:/).
2. See the [Description](https://github.com/moja-global/Land_Sector_Datasets/blob/master/Land_Sector_Data_Analysis/Land_Sector_Dataset_Description.md) of the datasets.
3. Refer to [past contributors' exploratory data analysis notebooks](https://github.com/moja-global/Handbook/issues/8#issuecomment-1328140024) of the Land Sector Datasets to learn how to get administrative and forest boundaries.

## Step 2: Install Example Version for Training

To install an example version for training, follow these steps:

1. Access the [Installation tools](https://github.com/moja-global/GCBM.Carpathians/releases/tag/install_tools).
2. Install the following example versions:
    * [GCBM.Carpathians](https://github.com/moja-global/GCBM.Carpathians)
    * [GCBM.Belize](https://github.com/moja-global/GCBM.Belize)
3. The installation guide is in the Standalone_GCBM/documentation folder of each example.
4. Ensure that you install all necessary prerequisites.

## Step 3: Select classifier

* Select a classifier for the simulation run. In this case, the classifier should be called `LifeZone`. Note that in the Youtube tutorial, the classifier is called `LdSpp`.

* Watch the first three videos of the Tutorial to adapting the GCBM template on [mojaglobal's youtube channel](https://www.youtube.com/playlist?list=PL_WECUlMWiUkIxULZzFrnu0IrfUjFRRXK)

* Modify the Tiler of a new simulation, run as necessary

## Step 4: Research key tree species and existing landscape
### Part 1: Approximating Growth Curves for Key Tree Types

To approximate growth curves for key tree types in your chosen forest, follow these steps:

1. Conduct a literature search to gather data on the amount of biomass for different age groups of the target tree species.
2. Normalize the data by area to obtain comparable biomass values on a per-hectare basis. Refer to this [guide](https://github.com/derha/GCBM.Carpathians.Data/blob/main/Tabular_Data/Tabular_Data.ipynb)
3. Use [Excel Solver](https://www.youtube.com/watch?v=VU1waW2WD-E&ab_channel=DescomplicaFlorestal) to solve initial guesses for curve fitting. If necessary, plug these numbers into `scipy.optimize.curve_fit()`. In rare cases when `scipy.optimize.curve_fit()` can't fit with these numbers, run Excel Solver again for new values.
4. Populate a growth curve table in Excel.
5. Convert volume to biomass if necessary using the transformation proposed by Boudewyn et al. Refer to section 2.5.2.2 of this [paper](https://www.researchgate.net/publication/341041237_Modelling_forest_carbon_dynamics_for_REDD_using_the_Generic_Carbon_Budget_Model_GCBM_Pilot_Project_Los_Rios_Region_-_Chile) for more information.
6. Export the data to a CSV file.

Please note that these steps are a general guide and may require modification based on your specific forest and tree types.

### Part 2: Holdridge Life zones
1. Find the Holdridge Life zones dataset from the [Land Sector Datasets](https://datasets.mojaglobal.workers.dev/0:)

2. Clip the Holdridge Life zones dataset to the boundaries of the forest of choice.

3. See past contributors' [exploratory data analysis notebooks](https://github.com/moja-global/Handbook/issues/8#issuecomment-1328140024) for how to clip datasets.
4. Rename the DESC column to LifeZone (the classifier), this is to link with the Growth Curve csv file in `Part 1` when running a simulation

5. Remove or fill empty rows as necessary

6. Add an Age column with all values as 0

Refer to the image below for clarity
![](https://i.imgur.com/YgiHVEP.png)

7. Export to shape file

### Part 3:Temperature layer

1. See past contributors' [exploratory data analysis notebooks](https://github.com/moja-global/Handbook/issues/8#issuecomment-1328140024) for how to clip raster layers and where to get the temperature dataset
2. Export to geotiff file

## Step 5: Combine all data, run system
1. Watch the first three videos of the Tutorial to adapting the GCBM template on [mojaglobal's youtube channel](https://www.youtube.com/playlist?list=PL_WECUlMWiUkIxULZzFrnu0IrfUjFRRXK)
2. Modify the Tiler of a new simulation run as necessary

## Step 6: Analyze results
1. Use the [GCBM.Belize Postprocessing R codes](https://github.com/moja-global/GCBM.Belize#postprocessing-and-sensitivity-analysis)

2. Use [SQL in Python](https://github.com/moja-global/GCBM.Belize/pull/7#issuecomment-1051436282) for various indicators

3. Use [Taswira](https://github.com/moja-global/taswira) to visualize

4. Here's a [case study](https://docs.google.com/document/d/1wKhmnXvP4mom1vaKz2gbVFzE_npyEDdmBtOTVinXX6Y/edit#heading=h.c7wb49aw32we) on how to interpret a forest's productivity


## Step 7: More detailed simulations
1. Steps 1-4
* Use multiple growth curves

2. Add disturbance layers

* Research fire events, invasive species, human economic activities...

* Watch the 4th and onward videos of the Tutorial to adapting the GCBM template on [mojaglobal's youtube channel](https://www.youtube.com/playlist?list=PL_WECUlMWiUkIxULZzFrnu0IrfUjFRRXK)

3. Add custom configurations

* Research woody biomass, AGB:BGB ratio, decay rate, mortality rate, probability and frequency of extreme events...

See [GCBM.Belize](https://github.com/moja-global/GCBM.Belize#custom-configuration-for-belize)

4. Run the simulation and analyze results

## Research On GCBM.UpperGuineanForest
* Here is a [link](https://github.com/Boluwape/GCBM.UpperGuineanForest/blob/main/GCBM.UpperGuineanForest/Tabular_Data/Growth_curves_data.ipynb) to growth curves of data extracted from research papers and all neccesary GCBM.UpperGuineanForest preprocessing steps

* Here is [link](https://drive.google.com/drive/folders/1T4RqV8K5loBOXf7S31O0BInN4ckFX09J?usp=sharing) to useful research papers
