# project_pigeon


# this is the demo client file



# # Importing Essentials
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.compose import ColumnTransformer
from sklearn.impute import SimpleImputer
from sklearn.preprocessing import OneHotEncoder

def drop_id_column(df_input):
    df_input.drop(['Id'], axis=1, inplace=True)
    return df_input

def count_missing_values(df_input):
    return df_input.isnull().sum()

def fill_missing_values_in_cat_columns(df_input):
    cat_columns = df_input.select_dtypes(include=['object']).columns
    print(cat_columns)
    for col in cat_columns:
        df_input[col] = df_input[col].fillna("None")
    return df_input

def main():
    housing = pd.read_csv(r"C:\MyPythonProjects\practice_folder\data\train.csv")
    #the following bit of code was abstracted out
    #housing.drop(['Id'], axis=1, inplace=True)
    drop_id_column(housing)
