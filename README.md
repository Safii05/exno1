# NAME:SAFIRA BARVEEN S
# #REGISTER NUMBER:212224230235
# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
          import pandas as pd
          import numpy as np
          import seaborn as sns
          import os 
          df=pd.read_csv("SAMPLEIDS.csv")
          df
```
![420870795-5f61f865-be8f-4a37-802e-ef47470625b3](https://github.com/user-attachments/assets/0964b427-edc6-4dd7-a244-59923150ce24)
```
         df.isnull().sum()
```
![420871365-2e8b90ed-f0f0-45f0-9af8-805a921d8890](https://github.com/user-attachments/assets/e9f47f48-6673-4235-be4b-e8de693e6ef6)
```
         df.isnull().any()
```

![420871482-705d9d1d-6a9e-49e3-84c9-ca9ce725b5a3](https://github.com/user-attachments/assets/206d4d68-7cb8-4202-b599-e28653cd1747)
```
         df.dropna()
```

![420871622-e47dde80-37c1-4b29-b155-fbe37caf8047](https://github.com/user-attachments/assets/cb8079be-6fb9-49ad-b14b-598c2b5a47e1)
```
         df.fillna(0)
```

![420988346-0f9ff748-510d-4e09-b8c0-47139dc97a08](https://github.com/user-attachments/assets/48cbfde8-bd66-46b3-ab77-01e08b3f1434)
```
         df.fillna(method = 'ffill')
```

![420988312-b6cfe900-a5f8-497e-beb3-6207103dedf9](https://github.com/user-attachments/assets/20967670-4b0a-4b09-8093-144861270d3e)
```
         df.fillna(method = 'bfill')
```

![420988571-dd78f399-c1a4-4204-ab9e-a3fb9cdec52e](https://github.com/user-attachments/assets/7bdce745-1ed4-4c68-905e-1b6457c67d2c)
```
         df_dropped = df.dropna()
           df_dropped
```

![420988659-64ce0243-dea5-49bd-9ec4-e795e1256686](https://github.com/user-attachments/assets/b9da9e7b-f3ea-4ab4-8381-70e6c09ecccf)
```
         df.fillna({'GENDER':'MALE','NAME':'KANISHKAR','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![420990395-43b3d48a-c134-4ee4-8815-c6e80aa1e32f](https://github.com/user-attachments/assets/d3115015-d5d8-4a99-ac15-367539aa3a7a)
```
         import pandas as pd
         
         ir=pd.read_csv('iris.csv')
         ir
```

![420990623-215096b4-ae49-4bbe-9d8a-00404f095b80](https://github.com/user-attachments/assets/819f161b-5bf4-4cbf-9e67-259bb8a7ca73)
```
         ir.describe()
```
![420990733-a3a2331b-947e-4a35-9218-d77942f2be76](https://github.com/user-attachments/assets/ef56b413-4401-4b78-a244-87a5ebbbe63d)
```
         import seaborn as sns
         
         sns.boxplot(x='sepal_width',data=ir)
```

![420990891-be8e43b0-0e7b-411f-97a9-46ad22f37652](https://github.com/user-attachments/assets/dfdd9771-e735-4084-a3e4-930ff71485df)

```
           c1=ir.sepal_width.quantile(0.25)
           c3=ir.sepal_width.quantile(0.75)
           iq=c3-c1
           print(c3)
```
3.3
```
            rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            rid['sepal_width']
```
![420991199-b94cd06f-1c5e-4a7b-88a3-046017a19e7e](https://github.com/user-attachments/assets/a7469198-57ae-4270-9b76-1351c4731386)
```
            delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
            delid
```

![420993240-9a4f0f5c-07fc-45c8-b217-830a87aa374f](https://github.com/user-attachments/assets/c4928a99-1381-4f5b-b3f9-0e7f89bf4f2f)
```
           sns.boxplot(x='sepal_width',data=delid)
```
![420993334-6a906ddf-2598-4267-a2a0-ca1b0b2d1193](https://github.com/user-attachments/assets/59b837bf-07e4-4ce2-8b6d-1c1ccdb7dd2f)
```
            import matplotlib.pyplot as plt
            import pandas as pd
            import numpy as np
            import scipy.stats as stats

            dataset=pd.read_csv("heights.csv")
            dataset
```

![420993496-9661074c-0f12-4d0c-be80-36d1c8c2d3b1](https://github.com/user-attachments/assets/f63cce15-9ec8-4482-84c8-ec62526e3e2e)
```
            df = pd.read_csv("heights.csv")
            q1 = df['height'].quantile(0.25)
            q2 = df['height'].quantile(0.5)
            q3 = df['height'].quantile(0.75)
            
            iqr = q3-q1
            iqr
```
0.9249999999999998
```
        low = q1 - 1.5*iqr
        low
```
3.8625000000000003
```
        high = q3 + 1.5*iqr
        high
```
7.5625
```
        df1 = df[((df['height'] >=low)& (df['height'] <=high))]
        df1
```

![420994093-a3bdff16-68b6-452c-92c8-760b411ef7fe](https://github.com/user-attachments/assets/60f1b18d-576b-4d23-80eb-74bd1ab34e17)
```
        z = np.abs(stats.zscore(df['height']))
        z
```

![420994190-76e7f2c0-5bbd-4322-a9fc-ffbaa503acdd](https://github.com/user-attachments/assets/5c0038ee-3229-472c-b3b8-94d912fb53dd)
```
        df1 = df[z<3]
        df1
```

![420994252-14fe1953-6f21-42f7-89d8-dab810a5647f](https://github.com/user-attachments/assets/f2326862-c76f-4646-9914-765c316f1fa5)

## RESULT
 
     Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
           







            

