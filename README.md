# DS_Airbnb-Analysis
DS_Airbnb Analysis
import pymongo
import pandas as pd
import matplotlib.pyplot as plt

# Connect to MongoDB
client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client["airbnb_database"]
collection = db["listings"]

# Fetch data from MongoDB and convert it to a pandas DataFrame
data = pd.DataFrame(list(collection.find()))

# Data cleaning and preprocessing (handle missing values, data types, etc.)
# For example:
# data.dropna(inplace=True)
# data['price'] = data['price'].str.replace('$', '').astype(float)

# Exploratory Data Analysis (EDA)
# For example:
# Summary statistics
print(data.describe())

# Visualizations
# For example:
# Histogram of prices
plt.hist(data['price'], bins=20)
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.title('Distribution of Prices')
plt.show()

# Feature Engineering
# For example:
# Extracting features from dates
data['year'] = pd.to_datetime(data['date']).dt.year
data['month'] = pd.to_datetime(data['date']).dt.month

# Modeling (if applicable)
# For example:
# Linear regression to predict prices based on features

# Evaluation (if applicable)
# For example:
# Evaluation metrics for regression model

# Close MongoDB connection
client.close()
