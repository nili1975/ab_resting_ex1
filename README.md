# ab_resting_ex1
import pandas as pd
import numpy as np
from scipy import stats

url='https://raw.githubusercontent.com/lazyprogrammer/machine_learning_examples/master/ab_testing/advertisement_clicks.csv'


df = pd.read_csv(url,index_col=False )
print(df.head(5))


df.to_excel(r'Q:\Data_science\ttest.xlsx',engine='xlsxwriter',index = False, header=True)


clicks_A = df[df['advertisement_id'] == 'A']['action']
clicks_B = df[df['advertisement_id'] == 'B']['action']

print("A_Mean",clicks_A.mean(),"B_Mean", clicks_B.mean())
print("A_std",clicks_A.std(),"B_std", clicks_B.std())

t, p = stats.ttest_ind(clicks_A, clicks_B)
print("t",t,"p", p)
