### Description

This Python script processes a dataset of prices, performing data cleaning, transformation, and encoding to make it suitable for machine learning. The script incorporates data wrangling techniques to handle categorical, temporal, and inconsistent data structures.


### Key Features

#### 1. **Data Import and Initial Cleanup**
- The dataset is loaded from an Excel file (`flight_price.xlsx`) using the `pandas` library.
- Unnecessary columns such as `Route` are permanently removed to streamline the dataset.

#### 2. **One-Hot Encoding of Categorical Variables**
- Categorical columns (`Airline`, `Source`, `Destination`, `Additional_Info`) are encoded using `OneHotEncoder` from `sklearn.preprocessing`.
- Encoded values are converted into a DataFrame for easy integration with the main dataset.

#### 3. **Handling Missing Values**
- The `Total_Stops` column is imputed with its mode to replace missing values.
- A mapping is applied to convert stop descriptions (`non-stop`, `1 stop`, etc.) into numerical equivalents.

#### 4. **Temporal Data Transformation**
- **Date of Journey**:
  - The `Date_of_Journey` column is split into day, month, and year components.
  - The components are converted into integers for compatibility with machine learning algorithms.
- **Departure Time**:
  - The `Dep_Time` column is split into hours and minutes and converted into integers.
- **Arrival Time**:
  - A lambda function is used to handle inconsistent structures in the `Arrival_Time` column, separating hours and minutes.

#### 5. **Duration Processing**
- The `Duration` column is split into hours and minutes using nested splitting techniques.
- Missing or inconsistent values are handled:
  - Missing `Duration_minute` values are imputed with their mode.
  - Irregular hour values like `5m` are corrected before conversion to integers.

#### 6. **Final Dataset Construction**
- Unnecessary columns (`Date_of_Journey`, `Dep_Time`, `Duration`, etc.) are dropped after feature extraction.
- Encoded categorical columns are concatenated with the main dataset to form the final DataFrame, `final_df`.



### Final Dataset Structure

The processed dataset includes:
1. One-hot encoded features for categorical variables.
2. Numeric representations of date, time, and stop-related data.
3. Cleaned and structured numerical features ready for machine learning models.


### Use Cases

- **Predictive Modeling**:
  - Estimate flight prices based on input features.
  - Optimize travel routes and time for cost efficiency.
- **Exploratory Analysis**:
  - Analyze relationships between features such as duration, stops, and price.
- **Data Preprocessing**:
  - Prepare datasets for advanced machine learning techniques, including regression or classification tasks.


### Notes

1. **Scalability**:
   - The script is robust enough to handle datasets with similar structures but may need minor adjustments for column naming conventions or unique value handling.



