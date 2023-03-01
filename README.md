# Stat1013 Project Part 1

</div>

<div class="cell markdown" id="yGuQlEMofqVI">

## Dataset background

**Description**

Data I have collected from The Chinese University of Hong Kong's and
Zhejiang Univercity's freshman students, which is about number of
courses they have taken this semester.

**Github:**
<https://github.com/Kitteniaa/STAT1013-Project-LYQ/blob/main/STAT1013Project1_LYQ.csv>

**sample size:** 60

**Feature documentation:**

| Feature                 | Class  | Shape | Dtype  |
|:------------------------|:-------|:------|:-------|
| School                  | Tensor |       | Object |
| Number of courses taken | Tensor |       | int64  |

</div>

<div class="cell markdown" id="4nqIxuzKlFQT">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   I'm interested in "*Do ZJU students take more courses than CUHK
        students per semester?*"
-   What two groups you are comparing:
    -   **G1**: Average number of courses taken by cuhk students ;
        **G2**: Average number of courses taken by zju students
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `Number of courses taken`
-   Is your response variable quantitative rather than categorical?
    -   Quantitative.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   I had expect that **G2** \> **G1** since [Chinese Mainland
        Students perceive heavier workload than other
        students](https://eric.ed.gov/?id=EJ1154552).
-   Talk about how you will gather your data
    -   I reserched it by myself and uploaded the data to github. Github
        link:
        <https://github.com/Kitteniaa/STAT1013-Project-LYQ/blob/main/STAT1013Project1_LYQ.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) I'll sample more comprehensively about students from
        different grade and major to get a better random sampling subset
        of these two populations.
    -   \(ii\) Attempt to collect more data for each population.

</div>

<div class="cell markdown" id="CgEtnO20tFbJ">

## Prepare my dataset

</div>

<div class="cell code" execution_count="10"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="lL-PhL04R2tu" outputId="acd186db-2ee0-49d7-cf77-4e2b1667449d">

``` python
import pandas as pd
df = pd.read_csv('https://raw.githubusercontent.com/Kitteniaa/STAT1013-Project-LYQ/main/STAT1013Project1_LYQ.csv')
df.head(5)
```

<div class="output execute_result" execution_count="10">

      School  Number of courses taken
    0   CUHK                        7
    1   CUHK                        8
    2   CUHK                        6
    3   CUHK                        6
    4   CUHK                        7

</div>

</div>

<div class="cell markdown" id="33yccwJ8vPUn">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (Number of courses taken \| school = CUHK) vs. **G2**
        (Number of courses taken \| school = ZJU)

</div>

<div class="cell markdown" id="m_I2SmqUvlts">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="14"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="6pB9PE4tvrPX" outputId="77dec907-6d51-4fd8-e612-408e3803f00a">

``` python
## First 5 records of G1 (cuhk)
(df[df['School'] == 'CUHK']['Number of courses taken']).head(5)
```

<div class="output execute_result" execution_count="14">

    0    7
    1    8
    2    6
    3    6
    4    7
    Name: Number of courses taken, dtype: int64

</div>

</div>

<div class="cell code" execution_count="13"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="W8JzMT7fwH9W" outputId="a45b52f1-71dc-4740-b205-83a80d5d371b">

``` python
## First 5 records of G2 (zju)
(df[df['School'] == 'ZJU']['Number of courses taken']).head(5)
```

<div class="output execute_result" execution_count="13">

    30    13
    31    15
    32    12
    33    13
    34    13
    Name: Number of courses taken, dtype: int64

</div>

</div>

<div class="cell code" execution_count="22"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="TltneQRKwb2E" outputId="16c2011d-7a8e-42e1-aae7-5c342a26e071">

``` python
## Any other data description and visualization you want to add.
df.info()
```

<div class="output stream stdout">

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 60 entries, 0 to 59
    Data columns (total 2 columns):
     #   Column                   Non-Null Count  Dtype 
    ---  ------                   --------------  ----- 
     0   School                   60 non-null     object
     1   Number of courses taken  60 non-null     int64 
    dtypes: int64(1), object(1)
    memory usage: 1.1+ KB

</div>

</div>

<div class="cell code" execution_count="33"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:279}"
id="o5HFCIKmzOWn" outputId="cf63e334-02d6-4b86-b33c-ea1d4298226b">

``` python
import seaborn as sns
import matplotlib.pyplot as plt

sns.stripplot(x=df['Number of courses taken'])
plt.show()
```

<div class="output display_data">

![](e9381035271e07166f6b27c0190224bba3bf8da4.png)

</div>

</div>

<div class="cell code" execution_count="34"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:279}"
id="U6OR6zfO15DG" outputId="41c24b13-93e8-4e13-d26a-3acbe1a17264">

``` python
sns.violinplot(data=df, x="School", y="Number of courses taken")
plt.show()
```

<div class="output display_data">

![](abae743f22f0bae01646819a254f78fea9de2fa5.png)

</div>

</div>
