
## <span style="font-family: Book Antiqua; font-size: 1em;">Survey Analysis</span>

<span style="font-family: Times New Roman; font-size: 1.2em;">Importing pandas and numpy libraries and reading the survey data into the dataframe - 'covidDF'</span>

```python

import pandas as pd

covidDF = pd.read_csv("COVID-19 Survey (Responses) - Form responses 1.csv")
covidDF.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="2" class="dataframe">
  <thead>
    <tr style="text-align: right; font-size: 12px">
      <th></th>
      <th>Timestamp</th>
      <th>What is your occupation?</th>
      <th>Where do you spend most of your free time?</th>
      <th>How much time do you spend on streaming services?</th>
      <th>How much time do you spend on gaming?</th>
      <th>How much time do you spend on social media?</th>
      <th>What are you most worried about during this time?</th>
      <th>ONE word that describes your mood right now.</th>
      <th>Where are you located ?</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;">
      <td>0</td>
      <td>29/03/2020 00:22:00</td>
      <td>Professional</td>
      <td>Other (Gardening, Cooking, Sleeping)</td>
      <td>&gt; 3 hours</td>
      <td>1 - 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>Family, Economy, Being stuck at home</td>
      <td>Happy</td>
      <td>NaN</td>
    </tr>
    <tr style = "font-size: 12px;">
      <td>1</td>
      <td>29/03/2020 00:26:52</td>
      <td>Student</td>
      <td>Online Courses (Coursera, LinkedIn Learning, U...</td>
      <td>&lt; 1 hour</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Job, Family, Being stuck at home</td>
      <td>Irritated</td>
      <td>NaN</td>
    </tr>
    <tr style = "font-size: 12px;">
      <td>2</td>
      <td>29/03/2020 00:37:44</td>
      <td>Professional</td>
      <td>Online Courses (Coursera, LinkedIn Learning, U...</td>
      <td>&gt; 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Job</td>
      <td>Bored</td>
      <td>NaN</td>
    </tr>
    <tr style = "font-size: 12px;">
      <td>3</td>
      <td>29/03/2020 00:38:23</td>
      <td>Home-maker</td>
      <td>Social Media (Twitter, Instagram, Facebook)</td>
      <td>&lt; 1 hour</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Family</td>
      <td>Depression</td>
      <td>NaN</td>
    </tr>
    <tr style = "font-size: 12px;">
      <td>4</td>
      <td>29/03/2020 00:38:35</td>
      <td>Professional</td>
      <td>Streaming services (Netflix, Amazon Prime, You...</td>
      <td>&gt; 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>&gt; 3 hours</td>
      <td>Job, Family</td>
      <td>Aimless</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

<br />
<span style="font-family: Times New Roman; font-size: 1.2em;">Checking if the dataframe has null values</span>

```python
covidDF.isnull().sum() 

```




    Timestamp                                             0
    What is your occupation?                              0
    Where do you spend most of your free time?            0
    How much time do you spend on streaming services?     4
    How much time do you spend on gaming?                 9
    How much time do you spend on social media?           3
    What are you most worried about during this time?     0
    ONE word that describes your mood right now.          0
    Where are you located ?                              65
    dtype: int64




```python
covidDF.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="2" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>Timestamp</th>
      <th>What is your occupation?</th>
      <th>Where do you spend most of your free time?</th>
      <th>How much time do you spend on streaming services?</th>
      <th>How much time do you spend on gaming?</th>
      <th>How much time do you spend on social media?</th>
      <th>What are you most worried about during this time?</th>
      <th>ONE word that describes your mood right now.</th>
      <th>Where are you located ?</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>count</td>
      <td>114</td>
      <td>114</td>
      <td>114</td>
      <td>110</td>
      <td>105</td>
      <td>111</td>
      <td>114</td>
      <td>114</td>
      <td>49</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>unique</td>
      <td>114</td>
      <td>7</td>
      <td>6</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>31</td>
      <td>87</td>
      <td>4</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>top</td>
      <td>29/03/2020 11:26:31</td>
      <td>Professional</td>
      <td>Other (Gardening, Cooking, Sleeping)</td>
      <td>1 - 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Family</td>
      <td>Bored</td>
      <td>USA</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>freq</td>
      <td>1</td>
      <td>64</td>
      <td>34</td>
      <td>57</td>
      <td>88</td>
      <td>55</td>
      <td>31</td>
      <td>9</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>



<br />
<span style="font-family: Times New Roman; font-size: 1.2em;">The last column 'ONE word that describes your mood right now.' is a free text field. However some respondents have replied in more than one word. 
We can edit this field by grouping similar words or feelings into a single word

```python
import re # RegEx

# creating a dataframe with only the required column which can be later merged with the original dataframe 'CovidDF'
one_word = pd.DataFrame(covidDF["ONE word that describes your mood right now."]).astype(str)

# The re.match function returns a 'None' if there is no match
for i in one_word.index: 
    if re.match( r'(.*)([Bb]or)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Bored"

```


```python
one_word # Let's have a look at the new dataframe
```



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>ONE word that describes your mood right now.</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>Happy</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>Irritated</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>Depression</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>Aimless</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>109</td>
      <td>Worried</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>110</td>
      <td>Okay</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>111</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>112</td>
      <td>Juggling</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>113</td>
      <td>Going with the flow</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 1 columns</p>
</div>

```python
```
<span style="font-family: Times New Roman; font-size: 1.2em;">Repeating the same steps to look for words that might have the similar meaning </span>




```python
	for i in one_word.index: 
		if re.match( r'(.*)([cC]onc)(.*)', str(one_word.iloc[i][0])) != None:
			one_word.iloc[i] = "Concerned"
		elif re.match( r'(.*)([wW]orr)(.*)', str(one_word.iloc[i][0])) != None:
			one_word.iloc[i] = "Worried"
		elif re.match( r'(.*)([sS]car)(.*)', str(one_word.iloc[i][0])) != None:
			one_word.iloc[i] = "Scared"

	one_word
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>ONE word that describes your mood right now.</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>Happy</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>Irritated</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>Depression</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>Aimless</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>109</td>
      <td>Worried</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>110</td>
      <td>Okay</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>111</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>112</td>
      <td>Juggling</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>113</td>
      <td>Going with the flow</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 1 columns</p>
</div>

```python
```
</br>
```python
for i in one_word.index:  
    if re.match( r'(.*)([gG]oo)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Good"
    elif re.match( r'(.*)([sS]ad)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Sad"

one_word
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>ONE word that describes your mood right now.</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>Happy</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>Irritated</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>Depression</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>Aimless</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>109</td>
      <td>Worried</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>110</td>
      <td>Okay</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>111</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>112</td>
      <td>Juggling</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>113</td>
      <td>Going with the flow</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 1 columns</p>
</div>


```python
```
</br>

```python
for i in one_word.index:   
    if re.match( r'([aA]nx)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Anxious"
    elif re.match( r'(.*)([hH]ap)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Happy"

one_word
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>ONE word that describes your mood right now.</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>Happy</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>Irritated</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>Depression</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>Aimless</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>109</td>
      <td>Worried</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>110</td>
      <td>Okay</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>111</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>112</td>
      <td>Juggling</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>113</td>
      <td>Going with the flow</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 1 columns</p>
</div>

```python
```
</br>


```python
for i in one_word.index:
    if re.match(r'(.*\s.*\s.*\S)', str(one_word.iloc[i][0])) != None:
        print([i],one_word.iloc[i][0])



```

    [10] Enjoying lockdown condition which never experienced in life
    [15] Learn something new 
    [27] Lazy and tired 
    [45] Feeling low due to current situation
    [47] Find a Cure for COVID-19
    [48] Optimistic that this phase will pass away one day. 
    [51] Faith in god
    [66] I am optimistic
    [69] Just want the country to do well
    [80] 80% Relaxed 20% anxious
    [89] Need work from home
    [101] Normal, as I am used to work from home 
    [105] Self descipline, face situation be prepaired
    [113] Going with the flow
    


```python
one_word.iloc[10] = "Enjoying"
one_word.iloc[15] = "Good"
one_word.iloc[27] = "Lazy"
one_word.iloc[45] = "Low"
one_word.iloc[47] = "Worried"
one_word.iloc[51] = "Hopeful"
one_word.iloc[66] = "Optimistic"
one_word.iloc[69] = "Hopeful"
one_word.iloc[80] = "Relaxed"
one_word.iloc[89] = "Stressed"
one_word.iloc[101] = "Normal"
one_word.iloc[105] = "Prepared"
one_word.iloc[113] = "Normal"

```


```python
for i in one_word.index:
    if re.match(r'(.*\s.*\S)', str(one_word.iloc[i][0])) != None:
        print([i],one_word.iloc[i][0])

```

    [22] Aai Baba
    [32] Active mood
    [48] Optimistic that this phase will pass away one day. 
    [61] optimistic, peaceful
    


```python
for i in one_word.index:   
    if re.match( r'([oO]pt)(.*)', str(one_word.iloc[i][0])) != None:
        one_word.iloc[i] = "Optimistic"
```


```python
one_word.iloc[22] = "Worried"
one_word.iloc[32] = "Active"

```


```python
one_word['ONE word that describes your mood right now.'].value_counts()
```




    Bored             20
    Worried            7
    Good               5
    Anxious            5
    Happy              5
    Optimistic         4
    Normal             4
    Chill              4
    Scared             3
    Relaxed            3
    Sad                2
    Hopeful            2
    Lazy               2
    Calm               2
    Tired              2
    Stressed           2
    Concerned          2
    bewildered         1
    Confused           1
    Pessimistic        1
    Depression         1
    Content            1
    Frustated          1
    claustrophobic     1
    Low                1
    Frustrated         1
    Tensed             1
    Aimless            1
    Exhausted          1
    Praying            1
    Imprisoned         1
    Prayerful.         1
    Okay               1
    Juggling           1
    Lazy               1
    Contented          1
    Annoyed            1
    Hungry             1
    Terrible           1
    Enjoing            1
    Aimless            1
    Lethargic          1
    Irritating         1
    Tension            1
    Angry              1
    Enjoying           1
    Irritated          1
    Calm               1
    Prepared           1
    Depleted           1
    Active             1
    HAPPY              1
    Busy               1
    Energetic          1
    Stressed           1
    Distancing         1
    Discouraged        1
    Name: ONE word that describes your mood right now., dtype: int64




```python
covidDF['Mood in One Word'] = one_word['ONE word that describes your mood right now.']

```


```python
covidDF.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>Timestamp</th>
      <th>What is your occupation?</th>
      <th>Where do you spend most of your free time?</th>
      <th>How much time do you spend on streaming services?</th>
      <th>How much time do you spend on gaming?</th>
      <th>How much time do you spend on social media?</th>
      <th>What are you most worried about during this time?</th>
      <th>ONE word that describes your mood right now.</th>
      <th>Where are you located ?</th>
      <th>Mood in One Word</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>29/03/2020 00:22:00</td>
      <td>Professional</td>
      <td>Other (Gardening, Cooking, Sleeping)</td>
      <td>&gt; 3 hours</td>
      <td>1 - 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>Family, Economy, Being stuck at home</td>
      <td>Happy</td>
      <td>NaN</td>
      <td>Happy</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>29/03/2020 00:26:52</td>
      <td>Student</td>
      <td>Online Courses (Coursera, LinkedIn Learning, U...</td>
      <td>&lt; 1 hour</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Job, Family, Being stuck at home</td>
      <td>Irritated</td>
      <td>NaN</td>
      <td>Irritated</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>29/03/2020 00:37:44</td>
      <td>Professional</td>
      <td>Online Courses (Coursera, LinkedIn Learning, U...</td>
      <td>&gt; 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Job</td>
      <td>Bored</td>
      <td>NaN</td>
      <td>Bored</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>29/03/2020 00:38:23</td>
      <td>Home-maker</td>
      <td>Social Media (Twitter, Instagram, Facebook)</td>
      <td>&lt; 1 hour</td>
      <td>&lt; 1 hour</td>
      <td>1 - 3 hours</td>
      <td>Family</td>
      <td>Depression</td>
      <td>NaN</td>
      <td>Depression</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>29/03/2020 00:38:35</td>
      <td>Professional</td>
      <td>Streaming services (Netflix, Amazon Prime, You...</td>
      <td>&gt; 3 hours</td>
      <td>&lt; 1 hour</td>
      <td>&gt; 3 hours</td>
      <td>Job, Family</td>
      <td>Aimless</td>
      <td>NaN</td>
      <td>Aimless</td>
    </tr>
  </tbody>
</table>
</div>



```python
        
```
</br>
```python
profession = ['Professional','Student','Home-maker','Retired']

for i in covidDF['What is your occupation?'].index:
    if covidDF.iloc[i][1] not in profession:
        print(i, covidDF.loc[i][1])
        
```

    13 Retired Mathematics Professor
    47 Business 
    57 Nurse practitioner 
    


```python
occ = pd.DataFrame(covidDF['What is your occupation?']).astype(str)

covidDF['What is your occupation?'].value_counts()

```




    Professional                     64
    Student                          35
    Home-maker                        7
    Retired                           5
    Retired Mathematics Professor     1
    Nurse practitioner                1
    Business                          1
    Name: What is your occupation?, dtype: int64




```python
occ.iloc[13]['What is your occupation?'] = "Retired"
occ.iloc[47]['What is your occupation?'] = "Professional"
occ.iloc[57]['What is your occupation?'] = "Professional"

covidDF['Occupation'] = occ['What is your occupation?']

covidDF['Occupation'].value_counts()

```




    Professional    66
    Student         35
    Home-maker       7
    Retired          6
    Name: Occupation, dtype: int64




```python
covidDF.isnull().sum()
```




    Timestamp                                             0
    What is your occupation?                              0
    Where do you spend most of your free time?            0
    How much time do you spend on streaming services?     4
    How much time do you spend on gaming?                 9
    How much time do you spend on social media?           3
    What are you most worried about during this time?     0
    ONE word that describes your mood right now.          0
    Where are you located ?                              65
    Mood in One Word                                      0
    Occupation                                            0
    dtype: int64




```python
covidDF.loc[covidDF['How much time do you spend on gaming?'] == '< 1 hour',('Where do you spend most of your free time?')]

```




    1      Online Courses (Coursera, LinkedIn Learning, U...
    2      Online Courses (Coursera, LinkedIn Learning, U...
    3            Social Media (Twitter, Instagram, Facebook)
    4      Streaming services (Netflix, Amazon Prime, You...
    5                   Other (Gardening, Cooking, Sleeping)
                                 ...                        
    108    Streaming services (Netflix, Amazon Prime, You...
    109                 Other (Gardening, Cooking, Sleeping)
    110                 Other (Gardening, Cooking, Sleeping)
    111    Streaming services (Netflix, Amazon Prime, You...
    112    Streaming services (Netflix, Amazon Prime, You...
    Name: Where do you spend most of your free time?, Length: 88, dtype: object




```python
covidDF['How much time do you spend on streaming services?'] = covidDF['How much time do you spend on streaming services?'].fillna('< 1 hour')

covidDF['How much time do you spend on streaming services?'].isnull().sum()

```




    0




```python
covidDF.isnull().sum()
```




    Timestamp                                             0
    What is your occupation?                              0
    Where do you spend most of your free time?            0
    How much time do you spend on streaming services?     0
    How much time do you spend on gaming?                 9
    How much time do you spend on social media?           3
    What are you most worried about during this time?     0
    ONE word that describes your mood right now.          0
    Where are you located ?                              65
    Mood in One Word                                      0
    Occupation                                            0
    dtype: int64




```python
covidDF['How much time do you spend on gaming?'] = covidDF['How much time do you spend on gaming?'].fillna('< 1 hour')

covidDF['How much time do you spend on gaming?'].isnull().sum()

```




    0




```python
covidDF['How much time do you spend on social media?'] = covidDF['How much time do you spend on social media?'].fillna('< 1 hour')

covidDF['How much time do you spend on social media?'].isnull().sum()

```




    0




```python
covidDF['What are you most worried about during this time?']

```




    0      Family, Economy, Being stuck at home
    1          Job, Family, Being stuck at home
    2                                       Job
    3                                    Family
    4                               Job, Family
                           ...                 
    109                                  Family
    110                                  Family
    111           Not necessary for you to know
    112              Unknown Consequences later
    113                    Job, Family, Economy
    Name: What are you most worried about during this time?, Length: 114, dtype: object




```python
c = covidDF['What are you most worried about during this time?'].value_counts()

c['Family'].sum()
c
```




    Family                                          31
    Economy                                         12
    Being stuck at home                             11
    Job, Family, Economy                             7
    Job                                              7
    Job, Family, Economy, Being stuck at home        7
    Family, Economy, Being stuck at home             5
    Job, Family                                      5
    Job, Family, Being stuck at home                 3
    Family, Economy                                  3
    Family, Being stuck at home                      2
    Job, Economy                                     2
    Health                                           1
    Overcoming the present situation                 1
    Lokha Sanastha dukkho Bhavantu                   1
    not worried as things will improve               1
    Uni                                              1
    Can’t travel                                     1
    How to keep healthy                              1
    Travel plans                                     1
    Job, Economy, Being stuck at home                1
    Job, Economy, Being stuck at home, My future     1
    When will the situation be under control         1
    Unknown Consequences later                       1
    To get more knowledge                            1
    Family, Education                                1
    Economy, Being stuck at home                     1
    Exams                                            1
    Study.                                           1
    Not necessary for you to know                    1
    Academic session and exams                       1
    Name: What are you most worried about during this time?, dtype: int64




```python
looper = covidDF['What are you most worried about during this time?']

Family = []

for i in looper.index:
    if re.match( r'(.*)[fF]am(.*)', str(looper.iloc[i])) != None:
        #print(looper.iloc[i])
        Family.append(1)
    else:
        Family.append(0)

print(Family)
      
```

    [1, 1, 0, 1, 1, 1, 1, 0, 1, 1, 0, 0, 0, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 1, 0, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 0, 1, 1, 1, 1, 1, 0, 1, 0, 0, 1, 0, 1, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 1, 1, 1, 0, 0, 1, 0, 0, 0, 0, 1, 1, 1, 0, 1, 1, 0, 0, 1]
    


```python
Economy = []

for i in looper.index: 
    #print(looper.iloc[i])
    if re.match( r'(.*)Econo(.*)', str(looper.iloc[i])) != None:
        #print(looper.iloc[i])
        Economy.append(1)
    else:
        Economy.append(0)

print(Economy)


```

    [1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 1, 1, 0, 1, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 1, 0, 1, 1, 0, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 1, 0, 1, 1, 1, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 1]
    


```python
Job = []

for i in looper.index:
    if re.match( r'(.*)Job(.*)', str(looper.iloc[i])) != None:
        Job.append(1)
    else:
        Job.append(0)

print(Job)


```

    [0, 1, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 1, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 1, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 1, 1, 1, 1, 0, 1, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1]
    


```python
Stuck = []

for i in looper.index:
    if re.match( r'(.*)Being\s[sS](.*)\s(.*)', str(looper.iloc[i])) != None:
        Stuck.append(1)
    else:
        Stuck.append(0)

print(Stuck)


```

    [1, 1, 0, 0, 0, 0, 1, 1, 0, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 0, 1, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 1, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0]
    


```python
other = []
       
for i in looper.index:
    if re.match( r'(.*)Being\s[sS](.*)\s(.*)', str(looper.iloc[i])) != None or re.match(r'(.*)Job(.*)', str(looper.iloc[i])) != None or re.match(r'Fam(.*)', str(looper.iloc[i])) != None or re.match(r'(.*)Econo(.*)', str(looper.iloc[i])) != None:
        other.append(0)
    else:
        other.append(1)
print(other)


```

    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 0]
    


```python
occupation_df = pd.DataFrame(list(zip(Stuck, Job, Economy, Family, other)), columns = ['Stuck','Job','Economy','Family','other'])

cat = occupation_df.sum()

cat.sum()

occupation_df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;font-size: 12px;">
      <th></th>
      <th>Stuck</th>
      <th>Job</th>
      <th>Economy</th>
      <th>Family</th>
      <th>other</th>
    </tr>
  </thead>
  <tbody>
    <tr style = "font-size: 12px;>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>2</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>109</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>110</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>111</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>112</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr style = "font-size: 12px;>
      <td>113</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 5 columns</p>
</div>




```python
covidDF[['Stuck','Job','Economy','Family','other']] = occupation_df[['Stuck','Job','Economy','Family','other']]

```


```python
covidDF

covidDF.to_csv('COVID19_SurveyResponses.csv')
```


```python
covidDF['Occupation'].value_counts()
```




    Professional    66
    Student         35
    Home-maker       7
    Retired          6
    Name: Occupation, dtype: int64




```python

```
