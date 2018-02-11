
# Academy of Py 


```python
# dependencies
import pandas as pd
```


```python
# read raw csv data files
students_csv = "/Users/stephaniechanshomefolder/Desktop/Pythonhw/students_complete.csv"
schools_csv = "/Users/stephaniechanshomefolder/Desktop/Pythonhw/schools_complete.csv"
```


```python
# create data frame 1
students_df=pd.read_csv(students_csv)
students_df.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
# create data frame 2
schools_df=pd.read_csv(schools_csv)
schools_df.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
# rename data frame 2 column for school
schools_dfrenamed = schools_df.rename(columns={
    "name":"school"
})
schools_dfrenamed.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>



# Create District Summary Dataframe


```python
# Variables to be values in dictionary
schools_counts = len(schools_df["name"].unique())
total_students = len(students_df["name"].unique())
total_budget = schools_df["budget"].sum()
ave_math = students_df["math_score"].mean()
ave_read = students_df["reading_score"].mean()
Pass_m = students_df.loc[(students_df["math_score"]>=70)]
Percent_m = round((len(Pass_m["name"].unique())/total_students)*100, 2)
Pass_r = students_df.loc[(students_df["reading_score"]>=70)]
Percent_r = round((len(Pass_r["name"].unique())/total_students)*100, 2)
Overall = (Percent_m + Percent_r)/2
```


```python
# make a dictionary to turn into dataframe
school_info_df = {"Total Schools": schools_counts, "Total Students": total_students,
                                 "Total Budget": total_budget, "Average Math Score": ave_math,
                                 "Average Reading Score": ave_read, "% Passing Math": Percent_m,
                                 "% Passing Reading": Percent_r,
                                 "Overall Passing Rate: (Average of the above two)": Overall}

district_summary = pd.DataFrame(school_info_df, index=[0])
district_summary
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Overall Passing Rate: (Average of the above two)</th>
      <th>Total Budget</th>
      <th>Total Schools</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>77.72</td>
      <td>87.38</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>82.55</td>
      <td>24649428</td>
      <td>15</td>
      <td>32715</td>
    </tr>
  </tbody>
</table>
</div>




```python
# merge data frame 1 and 2 together
merge_Academy = pd.merge(schools_dfrenamed, students_df, on="school")
merge_Academy.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe, Summary by School


```python
# Create variables to be values in Dictionary
schoolname = merge_Academy.groupby('school').count()
schooltype = merge_Academy.groupby('school')['type'].unique().str.get(0)
totalstudents = merge_Academy.groupby('school')['name'].count()
totalschoolbudt = merge_Academy.groupby('school')['budget'].unique().str.get(0)
perstudentbudt = totalschoolbudt/totalstudents.groupby('school').unique().str.get(0)
ave_math2 = merge_Academy.groupby('school')["math_score"].mean()
ave_read2 = merge_Academy.groupby('school')["reading_score"].mean()
Pass_m2 = merge_Academy.loc[(merge_Academy["math_score"]>=70)].groupby('school').count()
Pass_r2 = merge_Academy.loc[(merge_Academy["reading_score"]>=70)].groupby('school').count()
Percent_m2 = Pass_m2['math_score']/totalstudents*100
Percent_r2 = Pass_r2["reading_score"]/totalstudents*100
Overall2 = (Percent_m2 + Percent_r2)/2
```


```python
# make dictionary to turn into a dataframe
school_summary_df = pd.DataFrame({"School Type": schooltype, 
                     "Total Students": totalstudents, "Total School Budt.": totalschoolbudt,
                     "Budt. per Student": perstudentbudt, "Ave. Math Score": ave_math2,
                     "Ave. Read Score": ave_read2, "% Pass Math": Percent_m2, 
                     "% Pass Read": Percent_r2, "Overall %": Overall2})
school_summary_df
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Budt. per Student</th>
      <th>Overall %</th>
      <th>School Type</th>
      <th>Total School Budt.</th>
      <th>Total Students</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>628.0</td>
      <td>74.306672</td>
      <td>District</td>
      <td>3124928</td>
      <td>4976</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>582.0</td>
      <td>95.586652</td>
      <td>Charter</td>
      <td>1081356</td>
      <td>1858</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>639.0</td>
      <td>73.363852</td>
      <td>District</td>
      <td>1884411</td>
      <td>2949</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>644.0</td>
      <td>73.804308</td>
      <td>District</td>
      <td>1763916</td>
      <td>2739</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>625.0</td>
      <td>95.265668</td>
      <td>Charter</td>
      <td>917500</td>
      <td>1468</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>652.0</td>
      <td>73.807983</td>
      <td>District</td>
      <td>3022020</td>
      <td>4635</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>581.0</td>
      <td>94.379391</td>
      <td>Charter</td>
      <td>248087</td>
      <td>427</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>655.0</td>
      <td>73.500171</td>
      <td>District</td>
      <td>1910635</td>
      <td>2917</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>650.0</td>
      <td>73.639992</td>
      <td>District</td>
      <td>3094650</td>
      <td>4761</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>609.0</td>
      <td>95.270270</td>
      <td>Charter</td>
      <td>585858</td>
      <td>962</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>637.0</td>
      <td>73.293323</td>
      <td>District</td>
      <td>2547363</td>
      <td>3999</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>600.0</td>
      <td>94.860875</td>
      <td>Charter</td>
      <td>1056600</td>
      <td>1761</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>638.0</td>
      <td>95.290520</td>
      <td>Charter</td>
      <td>1043130</td>
      <td>1635</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>578.0</td>
      <td>95.203679</td>
      <td>Charter</td>
      <td>1319574</td>
      <td>2283</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>583.0</td>
      <td>94.972222</td>
      <td>Charter</td>
      <td>1049400</td>
      <td>1800</td>
    </tr>
  </tbody>
</table>
</div>



# Data Frame of Top Schools 


```python
topschoolsoverall_df = school_summary_df.sort_values(by="Overall %", ascending=False)
topschoolsoverall_df.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Budt. per Student</th>
      <th>Overall %</th>
      <th>School Type</th>
      <th>Total School Budt.</th>
      <th>Total Students</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Cabrera High School</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>582.0</td>
      <td>95.586652</td>
      <td>Charter</td>
      <td>1081356</td>
      <td>1858</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>638.0</td>
      <td>95.290520</td>
      <td>Charter</td>
      <td>1043130</td>
      <td>1635</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>609.0</td>
      <td>95.270270</td>
      <td>Charter</td>
      <td>585858</td>
      <td>962</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>625.0</td>
      <td>95.265668</td>
      <td>Charter</td>
      <td>917500</td>
      <td>1468</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>578.0</td>
      <td>95.203679</td>
      <td>Charter</td>
      <td>1319574</td>
      <td>2283</td>
    </tr>
  </tbody>
</table>
</div>



# Data Frame of Lowest Performing Schools 


```python
topschoolsoverall_df = school_summary_df.sort_values(by="Overall %")
topschoolsoverall_df.head()
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Budt. per Student</th>
      <th>Overall %</th>
      <th>School Type</th>
      <th>Total School Budt.</th>
      <th>Total Students</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Rodriguez High School</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>637.0</td>
      <td>73.293323</td>
      <td>District</td>
      <td>2547363</td>
      <td>3999</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>639.0</td>
      <td>73.363852</td>
      <td>District</td>
      <td>1884411</td>
      <td>2949</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>655.0</td>
      <td>73.500171</td>
      <td>District</td>
      <td>1910635</td>
      <td>2917</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>650.0</td>
      <td>73.639992</td>
      <td>District</td>
      <td>3094650</td>
      <td>4761</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>644.0</td>
      <td>73.804308</td>
      <td>District</td>
      <td>1763916</td>
      <td>2739</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe of each grade math score by school


```python
school_math_df = merge_Academy[['school', 'grade', 'math_score']]
school_math_df = school_math_df.groupby(['school', 'grade'])['math_score'].mean()
school_math_df.unstack()
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
    <tr style="text-align: right;">
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
      <td>77.083676</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
      <td>83.094697</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
      <td>76.403037</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
      <td>77.361345</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
      <td>82.044010</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
      <td>77.438495</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
      <td>83.787402</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
      <td>77.027251</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
      <td>77.187857</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
      <td>83.625455</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
      <td>76.859966</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
      <td>83.420755</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
      <td>83.590022</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
      <td>83.085578</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
      <td>83.264706</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe of each grade reading score by school


```python
school_read_df = merge_Academy[['school', 'grade', 'reading_score']]
school_read_df = school_read_df.groupby(['school', 'grade'])['reading_score'].mean()
school_read_df.unstack()
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
    <tr style="text-align: right;">
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
      <td>81.303155</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
      <td>83.676136</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
      <td>81.198598</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
      <td>80.632653</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
      <td>83.369193</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
      <td>80.866860</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
      <td>83.677165</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
      <td>81.290284</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
      <td>81.260714</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
      <td>83.807273</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
      <td>80.993127</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
      <td>84.122642</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
      <td>83.728850</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
      <td>83.939778</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
      <td>83.833333</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe of Budt. per Student


```python
bins = [550, 600, 650, 700]
group_name = ['550-600', '600-650', '650-700']
budgets = pd.cut(school_summary_df['Budt. per Student'], bins, labels = group_name)
budgets_df = pd.DataFrame({'Spending': budgets,
                           'Ave. Math Score': ave_math2, 
                           "Ave. Read Score": ave_read2, 
                           "% Pass Math": Percent_m2, 
                           "% Pass Read": Percent_r2, 
                           "Overall %": Overall2})
# Reset index and drop School column
budgets_df = budgets_df.reset_index().drop('school',1)
budgets_df
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
      <th>Spending</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>74.306672</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>95.586652</td>
      <td>550-600</td>
    </tr>
    <tr>
      <th>2</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>73.363852</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>3</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>73.804308</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>95.265668</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>5</th>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>73.807983</td>
      <td>650-700</td>
    </tr>
    <tr>
      <th>6</th>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>94.379391</td>
      <td>550-600</td>
    </tr>
    <tr>
      <th>7</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>73.500171</td>
      <td>650-700</td>
    </tr>
    <tr>
      <th>8</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>73.639992</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>9</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.270270</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>10</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>73.293323</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>11</th>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.860875</td>
      <td>550-600</td>
    </tr>
    <tr>
      <th>12</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>95.290520</td>
      <td>600-650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>95.203679</td>
      <td>550-600</td>
    </tr>
    <tr>
      <th>14</th>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>94.972222</td>
      <td>550-600</td>
    </tr>
  </tbody>
</table>
</div>




```python
budgets_df.groupby("Spending").mean()
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
    </tr>
    <tr>
      <th>Spending</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>550-600</th>
      <td>93.541501</td>
      <td>96.459627</td>
      <td>83.436210</td>
      <td>83.892196</td>
      <td>95.000564</td>
    </tr>
    <tr>
      <th>600-650</th>
      <td>76.832677</td>
      <td>86.725974</td>
      <td>79.423466</td>
      <td>82.044963</td>
      <td>81.779326</td>
    </tr>
    <tr>
      <th>650-700</th>
      <td>66.218444</td>
      <td>81.089710</td>
      <td>76.959583</td>
      <td>81.058567</td>
      <td>73.654077</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe of School Size


```python
bins2 = [0, 1000, 3000, 5000]
group_name2 = ['Small', 'Medium', 'Large']
size = pd.cut(school_summary_df['Total Students'], bins2, labels = group_name2)
size_df = pd.DataFrame({'Total Students': size,
                           'Ave. Math Score': ave_math2, 
                           "Ave. Read Score": ave_read2, 
                           "% Pass Math": Percent_m2, 
                           "% Pass Read": Percent_r2, 
                           "Overall %": Overall2})
# Reset index and drop School column
sizes_df = size_df.reset_index().drop('school',1)
sizes_df
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
      <th>Total Students</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>74.306672</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>1</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>95.586652</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>2</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>73.363852</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>3</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>73.804308</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>95.265668</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>5</th>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>73.807983</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>6</th>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>94.379391</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>7</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>73.500171</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>8</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>73.639992</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>9</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.270270</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>10</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>73.293323</td>
      <td>Large</td>
    </tr>
    <tr>
      <th>11</th>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.860875</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>12</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>95.290520</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>13</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>95.203679</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>14</th>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>94.972222</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
</div>




```python
sizes_df.groupby("Total Students").mean()
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
    </tr>
    <tr>
      <th>Total Students</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>93.550225</td>
      <td>96.099437</td>
      <td>83.821598</td>
      <td>83.929843</td>
      <td>94.824831</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>84.649798</td>
      <td>91.316412</td>
      <td>81.176821</td>
      <td>82.933187</td>
      <td>87.983105</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>66.464293</td>
      <td>81.059691</td>
      <td>77.063340</td>
      <td>80.919864</td>
      <td>73.761992</td>
    </tr>
  </tbody>
</table>
</div>



# Dataframe School Type


```python
types = school_summary_df['School Type']
types_df = pd.DataFrame({'School Type': types,
                           'Ave. Math Score': ave_math2, 
                           "Ave. Read Score": ave_read2, 
                           "% Pass Math": Percent_m2, 
                           "% Pass Read": Percent_r2, 
                           "Overall %": Overall2})
# Reset index and drop School column
types_df = types_df.reset_index().drop('school',1)
types_df
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
      <th>School Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>74.306672</td>
      <td>District</td>
    </tr>
    <tr>
      <th>1</th>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>95.586652</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>2</th>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>73.363852</td>
      <td>District</td>
    </tr>
    <tr>
      <th>3</th>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>73.804308</td>
      <td>District</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>95.265668</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>5</th>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>73.807983</td>
      <td>District</td>
    </tr>
    <tr>
      <th>6</th>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>94.379391</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>7</th>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>73.500171</td>
      <td>District</td>
    </tr>
    <tr>
      <th>8</th>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>73.639992</td>
      <td>District</td>
    </tr>
    <tr>
      <th>9</th>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>95.270270</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>10</th>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>73.293323</td>
      <td>District</td>
    </tr>
    <tr>
      <th>11</th>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>94.860875</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>12</th>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>95.290520</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>13</th>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>95.203679</td>
      <td>Charter</td>
    </tr>
    <tr>
      <th>14</th>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>94.972222</td>
      <td>Charter</td>
    </tr>
  </tbody>
</table>
</div>




```python
types_df.groupby("School Type").mean()
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
    <tr style="text-align: right;">
      <th></th>
      <th>% Pass Math</th>
      <th>% Pass Read</th>
      <th>Ave. Math Score</th>
      <th>Ave. Read Score</th>
      <th>Overall %</th>
    </tr>
    <tr>
      <th>School Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>93.620830</td>
      <td>96.586489</td>
      <td>83.473852</td>
      <td>83.896421</td>
      <td>95.103660</td>
    </tr>
    <tr>
      <th>District</th>
      <td>66.548453</td>
      <td>80.799062</td>
      <td>76.956733</td>
      <td>80.966636</td>
      <td>73.673757</td>
    </tr>
  </tbody>
</table>
</div>


