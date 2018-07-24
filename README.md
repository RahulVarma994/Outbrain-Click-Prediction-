# Outbrain-Click-Prediction-


import pandas as pd
import numpy as np
#importing data set
train = pd.read_csv('/media/FE5C77A55C77577D/outbrain/all/clicks_train.csv',usecols = ['ad_id','clicked'])
test = pd.read_csv('/media/FE5C77A55C77577D/outbrain/all/clicks_test.csv')


ad_aucc = train.groupby('ad_id').clicked.agg(['count','sum','mean']).reset_index()
Mean = train.clicked.mean()

ad_aucc['aucc'] = (ad_aucc['sum'] + 12*Mean) / (12 + ad_aucc['count'])


test = test.merge(ad_likelihood, how='left')
finaloutput = test.groupby('display_id').ad_id.apply(lambda x: " ".join(map(str,x))).reset_index()
finaloutput.to_csv('------------path/finaloutput',index = False )


## got an accuracy of 63.713
