# R Workshop 2024
Copyright 2024 Luiz Barboza, Andrew M. Olney and made available under [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0) for text and [Apache-2.0](http://www.apache.org/licenses/LICENSE-2.0) for code.

# Introduction

Block-based languages offer significant benefits for introducing programming concepts, especially to non-STEM learners. These languages use visual blocks to represent code, making the abstract nature of programming more tangible and accessible. By eliminating syntax errors and reducing the need for memorizing complex commands, they allow learners to focus on the logic and structure of programming. This visual and intuitive approach can lower the barrier to entry, making it easier for beginners to grasp fundamental concepts such as loops, conditionals, and variables. Additionally, block-based programming encourages experimentation and creativity, fostering a more engaging and enjoyable learning experience. As a result, non-STEM users can develop problem-solving skills and computational thinking without the intimidation often associated with traditional text-based coding.


Integrating Google Blockly with Jupyter Notebooks offers a range of advantages that enhance the programming and learning experience. Google Blockly provides a visual, block-based coding environment that simplifies the process of writing code by using draggable blocks to represent programming concepts. When combined with Jupyter Notebooks, this integration allows users to leverage the intuitive design of Blockly within the powerful, interactive framework of Jupyter. This synergy facilitates a smoother transition from visual programming to text-based coding, as learners can easily see the generated code alongside the blocks. It also promotes an interactive and iterative learning process, enabling users to run and test their code in real-time within the notebook environment. Moreover, this combination is particularly beneficial for educators and students, as it supports a variety of teaching methods and learning styles, making complex concepts more accessible and engaging. By lowering the entry barrier and fostering a hands-on approach to coding, Blockly integrated with Jupyter Notebooks empowers users to develop a deeper understanding of programming principles.

The transition from basic statistics to data science can seem overwhelming.
A significant part of the challenge is moving from traditional GUI-oriented programs like SPSS to programming-oriented environments.
This workshop reviews basic statistics in an advanced data science environment, [JupyterLab](https://jupyter.org/), using  blocks-based programming for the [R](https://www.r-project.org/) language. To use this notebook effectively, you should use the [Blockly extension](https://github.com/aolney/jupyterlab-blockly-r-extension) we have developed.
With this extension, you will be able to write *R* code by connecting blocks together.
Blocks-based programming removes some of the burden of learning to program (memorizing syntax, syntax errors, etc) and allows users to focus on solving data science problems. If you are not encountering this notebook in a live workshop, it is recommended that you watch this [short video tutorial](https://youtu.be/ovCJln08mG8?vq=hd720) or this [long video tutorial](https://youtu.be/-luPzplPDI0?vq=hd720) to see a demonstration, especially if you have never used a Jupyter notebook before.

Ready? Let's get started!

# Loading data

<details>
    <summary>Basics: Tabular data</summary>
    
The most common type of structured data is **tabular data** which is what you find in spreadsheets.
If you've ever used a spreadsheet, you know something about tabular data!

Here's an example of tabular data, with *height* in centimeters, *age* in years, and *weight* in kilograms:

| Height | Age | Weight |
|--------|-----|--------|
| 161    | 50  | 53     |
| 161    | 17  | 53     |
| 155    | 33  | 84     |
| 180    | 51  | 84     |
| 186    | 18  | 88     |

In tabular data like this, each **row** is a person.
More generically, we would say each row is an **observation** or **datapoint** (in statistics terminology) or an **item** (in machine learning terminology).
In each row, we have measurements for each of our variables for that particular person.
Since we have five rows of measurements, we know that there are five people in this dataset.

We can also think about tabular data in terms of **columns**.
Each column represents a variable, with the name of that variable in the **column header**.
For example, *height* is at the top of the first column and is the name of the variable for that column.
Importantly, the header is not an observation but rather a description of our data.
This is why we don't count the header when we are counting the rows in our data.

<details>
    <summary>Basics: Delimited tabular data</summary>

You are probably familiar with spreadsheet files, e.g. Microsoft Excel has files that end in `.xls` or `.xlsx`.
However, in data science, it is more common to have tabular data files that are **delimited**.
A delimited file is just a plain text file where column boundaries are represented by a specific character, usually a comma or a tab.

Here's an example of delimited tabular data, with *height* in centimeters, *age* in years, and *weight* in kilograms in **comma separated value (CSV)** form:

```
Height,Age,Weight
161,50,53
161,17,53
155,33,84
180,51,84
186,18,88
```

and here's what the data looks like in **tab separated value (TSV)** form:

```
Height	Age	Weight
161	50	53
161	17	53
155	33	84
180	51	84
186	18	88
```

The choice of the delimiter (comma, tab, or something else) is really arbitrary, but **it's always better to use a delimiter that doesn't appear in your data.**
</details>

First, let's read a CSV file into a dataframe.
A **dataframe** is variable that represents rows, columns, header, etc just like they are stored in a tabular data file.
To do that, we need to import a library called `readr`.
**If it isn't already open**, open up the Blockly extension.

<details>
    <summary>Basics: Open Blockly extension</summary>
    
Open up the Blockly extension by clicking on the painter's palette icon, then clicking on `Blockly R`.

![image.png](https://pbs.twimg.com/media/GQZSxkTXAAI-4t5?format=png&name=360x360)
<details>

## Importing a library

Using the IMPORT menu in the Blockly palette, click on an import block `library some library`:

![image.png](https://pbs.twimg.com/media/GQZTDUtWcAA-5BG?format=png&name=small)

When you click on the block, it drops onto the Blockly workspace.
Click on the `some library` dropdown, choose `Rename variable...`, and type `readr` into the box that pops up.
This imports the *R* `readr` library and gives it the variable name, or alias, `readr`.

In the future, we will abbreviate these steps as:

- `library readr`

Make sure the code cell below is selected (has a blue bar next to it) and press the `Blocks to Code` button below the Blockly workspace.
This will insert the code corresponding to the blocks into the **active cell** in Jupyter, which is the cell that has a blue bar next to it.

Once the code appears in the Jupyter cell below, you must **execute** or **run** it by either pressing the &#9658; button at the top of the window or by pressing Shift + Enter on your keyboard.

![lib_readr](https://pbs.twimg.com/media/GXYRB9mXwAAbY7A?format=png&name=240x240)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
library(readr)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="c}}IALaRyxW,6OvC9Na1">readr</variable></variables><block type="import_R" id="-Ov%#DvOj9;f!3`=#9Ox" x="93" y="38"><field name="libraryName" id="c}}IALaRyxW,6OvC9Na1">readr</field></block></xml>
```


## Reading a file

We can now do things with `readr`, like load datasets!

Our file is called `heart - train.csv` and it is in the `datasets` folder.
That means the **path** from this notebook (the one you're reading) to the data is `heart - train.csv`.

To read this file into a dataframe, we will use `readr`.
Go to the VARIABLES menu in the Blockly palette and click on the `with readr do ...` block.

![image.png](https://pbs.twimg.com/media/GQZUj0rW4AA2jVT?format=png&name=small)

After it drops into the Blockly workspace, wait until the dropdown stops loading, and then click on it and select `read_csv`.
You can also start typing `read_csv` to narrow the dropdown to matching options.
Then get a `" "` block from TEXT, drop it on the workspace, drag it to the `using` part of the first block, and type the file path `heart - train.csv` into it.
Your blocks should look like this:

![image.png](https://pbs.twimg.com/media/GQcSl0NWEAAVZfZ?format=png&name=small)

Make sure the cell below is selected, then press `Blocks to Codes`, and execute the cell to run the code by pressing the &#9658; button.

In the future, we will abbreviate these steps as:

- `with readr do read_csv using "heart - train.csv"`

*Note: the first time you use a library, it may take some time to load. You can see that R is working because the status bubble will be filled as shown below. When you load the library in the future, it will load instantly because we cache it.*

<!-- ![image.png](attachment:image.png) -->
![image.png](https://pbs.twimg.com/media/GQZU7vKXcAAG0TP?format=png&name=120x120)


```R
# Click here to start your blocks coding

```


    Error in parse(text = x, srcfile = src): <text>:1:8: unexpected '('
    1: readr::(
               ^
    Traceback:



**Rubrics**: 
```
readr::read_csv("heart - train.csv")

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="c}}IALaRyxW,6OvC9Na1">readr</variable></variables><block type="varDoMethod_R" id="!^Ma()y5gGVmg+~6_JTi" x="46" y="101"><mutation items="1"></mutation><field name="VAR" id="c}}IALaRyxW,6OvC9Na1">readr</field><field name="MEMBER">read_csv</field><data>readr:read_csv</data><value name="ADD0"><block type="text" id="$nncF$L$G8BVM0Q1oSO["><field name="TEXT">heart - train.csv</field></block></value></block></xml>
```

When you run the cell, it will display some information and then the dataframe directly below it.
This is one of the nice things about Jupyter - **it will display the output of the last line of code in a cell**, even if the output is text, a table, or a plot.

## Making a variable

Right now, we haven't actually stored the dataframe anywhere.
We used `readr` to read the csv file, and then Jupyter output that so we could see it.
But if we wanted to do anything with the dataframe, we'd have to read the file again.

Instead of reading the file every time we want to access the data, we can **store it in a variable**.
In other words, we will create a variable and set it to be the dataframe we created from the file.

Using VARIABLES menu in the Blockly palette, click on `Create variable...` and type `dataframe` into the pop up window.
Then click on the `set dataframe to` block so that your blocks below look like this:

![image.png](https://pbs.twimg.com/media/GQZVTthXYAAy9JV?format=png&name=240x240)

Then go get the same blocks you used before to read the file and connect them to the `set dataframe to` block.
You can do this from scratch or you can use the following procedure:

- Click the code cell below and press `Blocks to Code` to save your intermediate work (the `set dataframe to` block)
- Go back to the previous cell, click on the block you want, and copy it using Ctrl+c
- Click on the code cell below to select it, click the Blockly workspace, and paste the block using Ctrl+v

*Tip: If you don't save your intermediate work, you'll lose it because `Notebook Sync` will clear the Blockly workspace when it loads the blocks in the previous cell.*

After you've added the blocks to read the dataframe, drop a variable block for `dataframe` underneath it to display the dataframe.
The result should look like this:

![image.png](https://pbs.twimg.com/media/GQcSwlnWQAAbO_N?format=jpg&name=small)

In the future, we will abbreviate these steps as:

- Create `dataframe` and set it to `with readr do read_csv using "heart - train.csv.csv"`
- `dataframe`

As always, you need to hit the &#9658; button or press Shift + Enter to run the code.


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
dataframe = readr::read_csv("heart - train.csv")
print(dataframe);

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable><variable id="c}}IALaRyxW,6OvC9Na1">readr</variable></variables><block type="variables_set" id="U{gvKvTUz_RaN|r.LFO;" x="27" y="91"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field><value name="VALUE"><block type="varDoMethod_R" id="qn~Au$wL2M@Ovku]Q*:S"><mutation items="1"></mutation><field name="VAR" id="c}}IALaRyxW,6OvC9Na1">readr</field><field name="MEMBER">read_csv</field><data>readr:read_csv</data><value name="ADD0"><block type="text" id="Wo*-Q3-nxY57cXg$9u2m"><field name="TEXT">heart - train.csv</field></block></value></block></value><next><block type="text_print" id="9q=*wZ[F)laOd3|Kwlcl"><value name="TEXT"><shadow type="text" id="7mLHIs?rE!dR%l;V/wAN"><field name="TEXT">abc</field></shadow><block type="variables_get" id="XMkbF`_]_KaW^[.Jhkqd"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value></block></next></block></xml>
```

You should see the same output as before - the only difference is that we've read the csv and stored the data into the `dataframe` block, so we will use the `dataframe` block whenever we want to work with the data.

## Recap: Loading data

When you want to load data in the future, simply do the following:

- library `readr` *(loads the library)*
- Set `dataframe` to with `readr` do `read_csv` using `your data file name` *(loads the dataframe)*
- `dataframe` *(displays the dataframe)*

# Data Manipulation

**About Dataset**

Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worldwide. Four out of 5CVD deaths are due to heart attacks and strokes, and one-third of these deaths occur prematurely in people under 70 years of age. Heart failure is a common event caused by CVDs and this dataset contains 11 features that can be used to predict a possible heart disease.

People with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidaemia or already established disease) need early detection and management wherein a machine learning model can be of great help.

**Attribute Information**
- ***Age***: age of the patient [years]
- ***Sex***: sex of the patient [M: Male, F: Female]
- ***ChestPainType***: chest pain type [TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic]
- ***RestingBP***: resting blood pressure [mm Hg]
- ***Cholesterol***: serum cholesterol [mm/dl]
- ***FastingBS***: fasting blood sugar [1: if FastingBS > 120 mg/dl, 0: otherwise]
- ***RestingECG***: resting electrocardiogram results [Normal: Normal, ST: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV), LVH: showing probable or definite left ventricular hypertrophy by Estes' criteria]
- ***MaxHR***: maximum heart rate achieved [Numeric value between 60 and 202]
- ***ExerciseAngina***: exercise-induced angina [Y: Yes, N: No]
- ***Oldpeak***: oldpeak = ST [Numeric value measured in depression]
- ***ST_Slope***: the slope of the peak exercise ST segment [Up: upsloping, Flat: flat, Down: downsloping]
- ***HeartDisease***: output class [1: heart disease, 0: Normal]

**Origin**
This dataset was created by combining different datasets already available independently but not combined before. In this dataset, 5 heart datasets are combined over 11 common features which makes it the largest heart disease dataset available so far for research purposes. The five datasets used for its curation are:
- Cleveland: 303 observations
- Hungarian: 294 observations
- Switzerland: 123 observations
- Long Beach VA: 200 observations
- Stalog (Heart) Data Set: 270 observations

Total: 1190 observations

Duplicated: 272 observations

Final dataset: 918 observations

Every dataset used can be found under the Index of heart disease datasets from UCI Machine Learning Repository on the following link: https://archive.ics.uci.edu/dataset/145/statlog+heart

**Acknowledgements**:
- Hungarian Institute of Cardiology. Budapest: Andras Janosi, M.D.
- University Hospital, Zurich, Switzerland: William Steinbrunn, M.D.
- University Hospital, Basel, Switzerland: Matthias Pfisterer, M.D.
- V.A. Medical Center, Long Beach and Cleveland Clinic Foundation: Robert Detrano, M.D., Ph.D.
- Donor:
David W. Aha (aha '@' ics.uci.edu)

**Source**

https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction

## Filter Rows

There are many things we can do with dataframes.
One thing we can do is get specific rows, which are our datapoints.
We can manipulate dataframes easily using another library called `dplyr`, so let's load it first:

- `library dplyr`

*Then &#9658; or Shift + Enter*

![lib-delyr](https://pbs.twimg.com/media/GXYTmrPWMAAD26x?format=png&name=240x240)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
library(dplyr)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable></variables><block type="import_R" id="b8{o77H?}0sq(bP/@|ld" x="79" y="58"><field name="libraryName" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field></block></xml>
```

Don't worry too much about the messages displayed pink at this point.

Let's get the first row of the dataframe.
We can do that using the `slice` function:

- with `dplyr` do `filter` using `dataframe` and freestyle `Age>70`

To get an extra slot for `Age>70`, use the `+` button on the block.

Your blocks should look like this:

![image.png](https://pbs.twimg.com/media/GQcUeGmXQAAVFmV?format=png&name=small)

*Make sure the code cell below is selected, then &#9658; or Shift + Enter*


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
dplyr::filter(dataframe,Age>70)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="varDoMethod_R" id="=UkrUNji]ZRt=LB)4POl" x="60" y="150"><mutation items="2"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">filter</field><data>dplyr:filter</data><value name="ADD0"><block type="variables_get" id="MmJs.I|l0:,(-%x7@)Pu"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="i=)97fF6ah!b}as=Vsed"><field name="CODE">Age&gt;70</field></block></value></block></xml>
```

As you can see, the output is only the grades above 7 (seven)


## Selecting columns

Similarly, we can get a column of the dataframe by using the name of that column in a freestyle block.
The name must **exactly** match the spelling and case of the column:

- with `dplyr` do `select` using `dataframe` and `HeartDisease`

![](https://pbs.twimg.com/media/GQcUQxKWQAA6lBD?format=png&name=small)

And run it.


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
dplyr::select(dataframe,HeartDisease)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="varDoMethod_R" id="q)p=`rH?LPP4Gn4WwxjY" x="72" y="149"><mutation items="2"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">select</field><data>dplyr:select</data><value name="ADD0"><block type="variables_get" id="Mut7c1N%FD?gQCcm$6V5"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="cXnQ|a1oE(1OYTCbd!ic"><field name="CODE">HeartDisease</field></block></value></block></xml>
```

Putting together the **row filtering** and the **column selection**, as follow:

![](https://pbs.twimg.com/media/GXYkZ-yWUAEHZlf?format=jpg&name=medium)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
dplyr::select(dplyr::filter(dataframe,Age>70),HeartDisease)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="varDoMethod_R" id="VPuB]S,.)w2I|q*CZ*Dn" x="50" y="91"><mutation items="2"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">select</field><data>dplyr:select</data><value name="ADD0"><block type="varDoMethod_R" id="=Dm=@*6Ax~LZN@77rfY_"><mutation items="2"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">filter</field><data>dplyr:filter</data><value name="ADD0"><block type="variables_get" id="DRr^Gd!hKrQ)Cm!FI7KN"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id=":on*XRYj=:Hm.vG=lD)]"><field name="CODE">Age&gt;70</field></block></value></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="uT,o|I5u:p6d}x53MBz["><field name="CODE">HeartDisease</field></block></value></block></xml>
```

##  Pipe Operator (%>%)

The R pipe operator (`%>%`), from the `magrittr` and `dplyr` packages, allows for more readable and concise code by passing the output of one function directly into the next. This enables a clear, left-to-right flow of data transformations, making sequences of operations easier to understand and maintain. Instead of nested functions like `f(g(h(x)))`, you can write `x %>% h() %>% g() %>% f()`, simplifying both code readability and debugging.

Let's re-connect the **filter** with the **select** using `%>%` (pipes)  

![](https://pbs.twimg.com/media/GQcVu2cXUAAImEQ?format=png&name=900x900)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
dataframe %>%
    dplyr::filter(Age>70) %>%
    dplyr::select(HeartDisease)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="pipe_R" id="!/NZ`d8`,vdy3xR{w~sH" x="82" y="143"><mutation items="2"></mutation><value name="INPUT"><block type="variables_get" id="@6,[FKc@nUnr.Q(Ny@mK"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD0"><block type="varDoMethod_R" id="82T]cFmWXn8k_qN4@J8="><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">filter</field><data>dplyr:filter</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="S`t;.eaP|)#@vE}k7]K,"><field name="CODE">Age&gt;70</field></block></value></block></value><value name="ADD1"><block type="varDoMethod_R" id="`^^MVzEQuZ.)XvbHFqeG"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">select</field><data>dplyr:select</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="AUENt{nj6AziSq)w3Pq6"><field name="CODE">HeartDisease</field></block></value></block></value></block></xml>
```


## Data Consolidation / Summarization

Using the `group_by` operator is essential in data analysis for organizing data by a categorical column and summarizing it with a numerical one. By grouping data this way, analysts can apply mathematical functions like means, medians, or sums to each group, uncovering patterns and trends within the dataset. This approach helps to highlight key differences and similarities across segments, making the results clearer and more interpretable, thus facilitating better decision-making.

![](https://pbs.twimg.com/media/GQcY-zpXEAEk_LV?format=jpg&name=small)



```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
avgHR = dataframe %>%
    dplyr::group_by(HeartDisease) %>%
    dplyr::summarise(agv=mean(MaxHR))

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="ocR_fh#Y),ii!ZBEj{k9">avgHR</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable></variables><block type="variables_set" id="?~cPV];AEtx*Jkc]GPgs" x="51" y="49"><field name="VAR" id="ocR_fh#Y),ii!ZBEj{k9">avgHR</field><value name="VALUE"><block type="pipe_R" id="[Rz`(-@dn58TNN9[,YoJ"><mutation items="2"></mutation><value name="INPUT"><block type="variables_get" id=";/}k8^vJqs]lihOZMpi-"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD0"><block type="varDoMethod_R" id="`[g1umF6W)GRoM3W0H$j"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">group_by</field><data>dplyr:group_by</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="]P0H%f@P{D^OE4)J2TLf"><field name="CODE">HeartDisease</field></block></value></block></value><value name="ADD1"><block type="varDoMethod_R" id="AD:j?~_.fL9mi!VY,z/N"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">summarise</field><data>dplyr:summarise</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="rw,;29qLDinfB[(m,T,u"><field name="CODE">agv=mean(MaxHR)</field></block></value></block></value></block></value></block></xml>
```

## Recap: Data Manipulation

Dataframes are both lists of rows and lists of columns.
Whether we treat a dataframe as a list of rows or list of columns depends on what we want to do.
If we want to select datapoints (observations), then we treat it as a list of rows, because each row is a datapoint.
In our dataset above, this would be like selecting the people in the dataset we want to analyze, since each row is a person.
In contrast, if we want to select variables, then we treat the dataframe like a list of columns.

# Plotting

Data visualization is the discipline of trying to understand data by using graphic context so patterns, trends, and correlations that might not otherwise be detected can be exposed.

Data visualization is an important tool to understand data.

Charts, plots, graphs, and maps (and many more) are all types of data visualizations.

There are many facets involved in data visualization; this tutorial is just the introduction in your R plotting journey.

Today we will focus on the most often used plots:

- Bar plots
- Line plots
- Pie charts

*Each type of plot requires a specific type of data and has a specific purpose.*

In R, there are many options for visualizing data and is often challenging to choose which library to use.

For the purpose of this tutorial, we will focus on understanding, programming, and interpreting plots from `ggplot2`.

To use `ggplot2`,

- `library ggplot2`

![lib_gg](https://pbs.twimg.com/media/GXfJhUbW0AAYFOR?format=png&name=360x360)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
library(ggplot2)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable></variables><block type="import_R" id="4BbTBFgATV.cyBQLb|8T" x="61" y="30"><field name="libraryName" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field></block></xml>
```

The `ggplot2` package in R is a powerful tool for creating a wide range of static, interactive, and animated graphics. Its basic usage involves initializing a plot with the `ggplot()` function, specifying the dataset and aesthetic mappings (using `aes()`) to define how data variables are mapped to visual properties like the x and y axes. Layers are then added to the plot using `geom_` functions (e.g., `geom_point()` for scatter plots, `geom_bar()` for bar charts), which specify the type of plot. Additional customization can be applied through themes and scales to adjust colors, labels, and other stylistic elements. This structured approach to building plots makes `ggplot2` highly flexible and powerful for data visualization.

[Reference material for ggplot2](http://www.sthda.com/english/wiki/ggplot2-essentials)

## Bar plots

Bar plots are very commonly used in both science and the business world.

Bar plots:

- Require the x to be discrete values
- Require the y to be a single number per x
- Are best for showing summary values like averages

In other words, while scatterplots show all the datapoints, bar plots only show a **summary value of y** for each x.

Let's make a bar plot using the average, or `mean` of the variables as a summary value.

![](https://pbs.twimg.com/media/GQcZb7lW0AAsh_y?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(avgHR,aes(x=HeartDisease,y=agv,fill=HeartDisease)) +
    geom_bar(stat='identity')

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="ocR_fh#Y),ii!ZBEj{k9">avgHR</variable></variables><block type="ggplot_plus_R" id="2FS4ym|_{=Z@GE0[FAj!" x="24" y="72"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="DdVL~/YX7G)zmg-9xQMA"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="#SC5ZX#Gniqg6~@7@.ku"><field name="VAR" id="ocR_fh#Y),ii!ZBEj{k9">avgHR</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="X/1W__gm{ZgW)GYb+ju]"><field name="CODE">aes(x=HeartDisease,y=agv,fill=HeartDisease)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="v1Cw(6cf3U]ESg!AO+sQ"><field name="CODE">geom_bar(stat='identity')</field></block></value></block></xml>
```

The **stat** parameter `identity` is applicable here because we had the data already summarized. In case we need to **ggplot** to summarize the data at the same time the plot is generated it is possible to do so with **stat** parameter as `summary` and the parameter **fun** (function)

![](https://pbs.twimg.com/media/GQcZ187XEAAo8h3?format=jpg&name=small)

 


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(dataframe,aes(x=HeartDisease,y=MaxHR,fill=HeartDisease)) +
    geom_bar(stat="summary",fun="mean")

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="ggplot_plus_R" id="H+H67XJF!aD7u4k4Fx?`" x="79" y="124"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="o~aQ2?!E8ou|P.:osxYE"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="Y=CP;~L:${T/,`n@RF4y"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id=")aPQl*e.UXPJ:-/tucxs"><field name="CODE">aes(x=HeartDisease,y=MaxHR,fill=HeartDisease)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="6.y8cYau!m0ShcerqUF@"><field name="CODE">geom_bar(stat="summary",fun="mean")</field></block></value></block></xml>
```

## Pie Chart

A pie chart is a circular graph that visually represents proportions or percentages of a whole. It is divided into slices to illustrate the distribution of categories within the dataset. Each slice corresponds to a category or group, and its size is proportional to the quantity it represents relative to the whole. Pie charts are effective for conveying simple comparisons at a glance but can become less effective with too many categories or when trying to compare slices that are similar in size. They are commonly used in presentations and reports to highlight relative proportions, such as market shares, survey responses, or budget allocations.

Let's start summarizing the data:

![](https://pbs.twimg.com/media/GQcbFF5WkAEjTVC?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
count_gender_with_disease = dataframe %>%
    dplyr::filter(HeartDisease>0) %>%
    dplyr::group_by(Sex) %>%
    dplyr::summarise(qty=NROW(Sex))
print(count_gender_with_disease);

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="oup7i5t?*TI}@LPRoQrH">count_gender_with_disease</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable><variable id="eiVd%}K(~]c3]fWPwEgG">dplyr</variable></variables><block type="variables_set" id="PH1ns{drX]tx|vNM+P-g" x="35" y="83"><field name="VAR" id="oup7i5t?*TI}@LPRoQrH">count_gender_with_disease</field><value name="VALUE"><block type="pipe_R" id="Rx14hu#wSO,xS0f4``UN"><mutation items="3"></mutation><value name="INPUT"><block type="variables_get" id="GvGdxrs(::Nm)CCur1DR"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD0"><block type="varDoMethod_R" id="q1cHVJr:[HJuW!{pXf(w"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">filter</field><data>dplyr:filter</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="*dKr0DKgw!/%WoGL}x`;"><field name="CODE">HeartDisease&gt;0</field></block></value></block></value><value name="ADD1"><block type="varDoMethod_R" id="?Q(;j)5@E[8UmJ%z_n~T"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">group_by</field><data>dplyr:group_by</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="Mo:En___DCWjV;?Qz4;$"><field name="CODE">Sex</field></block></value></block></value><value name="ADD2"><block type="varDoMethod_R" id="|ouc$MPQ0wU{19ssF*w@"><mutation items="1"></mutation><field name="VAR" id="eiVd%}K(~]c3]fWPwEgG">dplyr</field><field name="MEMBER">summarise</field><data>dplyr:summarise</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id=".BUW/,22|kGp+QcDyA6q"><field name="CODE">qty=NROW(Sex)</field></block></value></block></value></block></value><next><block type="text_print" id="1pIs1=Hcy/9$22b$unTQ"><value name="TEXT"><shadow type="text" id=",0)rTn/W`cpRN~uFP,V~"><field name="TEXT">abc</field></shadow><block type="variables_get" id="S:=4=)64-loso8n8sUi="><field name="VAR" id="oup7i5t?*TI}@LPRoQrH">count_gender_with_disease</field></block></value></block></next></block></xml>
```

`ggplot2` does not have a built-in pie chart function, so to create a pie chart-like visualization, a bar plot can be adapted using `coord_polar()` to transform it into a circular layout and `geom_text()` for labeling proportions as percentages of the total.

The `geom_text()` should define the aesthetic as `aes(label = qty/sum(qty)*100),position=position_stack(vjust = 0.5)` as calculating the percentage of each quantity (qty) relative to the total quantity and using that as the label for each slice of the pie, and adjusting the position of the labels within the slices.

![](https://pbs.twimg.com/media/GQcbaVeWwAA-Rm9?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(count_gender_with_disease,aes(x="",y=qty,fill=Sex)) +
    geom_bar(stat="identity") +
    coord_polar("y") +
    geom_text(aes(label=qty/sum(qty)*100),position=position_stack(vjust=0.5))

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="oup7i5t?*TI}@LPRoQrH">count_gender_with_disease</variable></variables><block type="ggplot_plus_R" id="UJ4T88L8dxG+8^wf4Hv(" x="97" y="137"><mutation items="3"></mutation><value name="INPUT"><block type="varDoMethod_R" id="$279TU59!d:J57*_lyy!"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="J6O=*`s7g=:,MMf.-%}V"><field name="VAR" id="oup7i5t?*TI}@LPRoQrH">count_gender_with_disease</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="GldP77/aTe{;t`8:|`b;"><field name="CODE">aes(x="",y=qty,fill=Sex)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="42*)|5{7k]lGCt}_xZ;L"><field name="CODE">geom_bar(stat="identity")</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="Nn+0Xsolg8#9Q52RcjyB"><field name="CODE">coord_polar("y")</field></block></value><value name="ADD2"><block type="dummyOutputCodeBlock_R" id="N)}YmKa%/d%s{li}lauC"><field name="CODE">geom_text(aes(label=qty/sum(qty)*100),position=position_stack(vjust=0.5))</field></block></value></block></xml>
```

## Line plots

Line plots are virtually identical to bar plots in usage because they:

- Require the x to be discrete values
- Require the y to be a single number per x
- Are best for showing summary values like averages

However, line plots, unlike bar plots, have the advantage that you can show multiple **sets** of lines at once.
In a bar plot, these would be overlapping, and patterns would be potentially difficult to see.

Making a line plot is very similar to a bar plot.

Let's load another dataframe (df), `covid.csv

![covid](https://pbs.twimg.com/media/GXfJ9HJWkAA_4BR?format=jpg&name=medium)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
covid = readr::read_csv("covid.csv")
print(covid);

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="+,WfrKu=AEz:tuJsz$3R">covid</variable><variable id="c}}IALaRyxW,6OvC9Na1">readr</variable></variables><block type="variables_set" id="f=6wb9d:UW3Q)06{iE^Z" x="24" y="179"><field name="VAR" id="+,WfrKu=AEz:tuJsz$3R">covid</field><value name="VALUE"><block type="varDoMethod_R" id="[YgA{_7z8e/R;yK1l9;o"><mutation items="1"></mutation><field name="VAR" id="c}}IALaRyxW,6OvC9Na1">readr</field><field name="MEMBER">read_csv</field><data>readr:read_csv</data><value name="ADD0"><block type="text" id="f71$005JKojPRt?V9j/;"><field name="TEXT">covid.csv</field></block></value></block></value><next><block type="text_print" id="/|Sl`^RiMB6nF*y^LU.W"><value name="TEXT"><shadow type="text" id="ObHe7z~,+.n7mJTD=HJx"><field name="TEXT">abc</field></shadow><block type="variables_get" id="baK$Z4bp=uquTm.2HD[I"><field name="VAR" id="+,WfrKu=AEz:tuJsz$3R">covid</field></block></value></block></next></block></xml>
```

Here `ggplot2` nicely draws each variable in its own color, so we can see that all variables except `SepalWidth` seem to increase across species.

There are two important points to make here:

- Normally in line plots, the x axis is an ordered variable, like year. With a nominal variable like `Species`, we are fortunate to get such nice lines and not "spaghetti."

- Drawing multiple lines at once on one plot only makes sense if the variables have the same units of measurement, here centimeters. Otherwise the plot can mislead anyone not looking closely at the y axis.

See the below the covid cases line plot for US, Brazil and India:

![](https://pbs.twimg.com/media/GQcfEKiW8AAphyK?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(covid,aes(x=date,y=values,group=variable,color=variable)) +
    geom_line()

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="+,WfrKu=AEz:tuJsz$3R">covid</variable></variables><block type="ggplot_plus_R" id="`yjz$N`v!oj@,M2Ah],Z" x="50" y="93"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="eg]}:!=XT0;!aGx]Slr;"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="V`f4d)q{3WM;U*1XNRz]"><field name="VAR" id="+,WfrKu=AEz:tuJsz$3R">covid</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="L?v:$8%L(AhJ@^0-ecHd"><field name="CODE">aes(x=date,y=values,group=variable,color=variable)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="X^E@~ihkV=kkdW!Q$pz@"><field name="CODE">geom_line()</field></block></value></block></xml>
```

## Recap: Plotting

There are many types of plots, and which you should choose depends on the variables you want to visualize as well as the purpose of your visualization:


- Bar plots show a single value for each x, typically an average or other summary value
- Line plots are like bar plots but have an advantage for showing multiple lines at once


An important type of plot, the boxplot, was not discussed here because it requires a foundation in descriptive statistics, which we will cover next.

# Statistical Graphs

Two of the essential statistical graphs used to visualize distributions and summarize data characteristics, histograms and boxplots. Histograms visualize the distribution of numerical data by grouping values into bins and showing the frequency of values in each bin. They reveal patterns in data such as skewness and central tendency. Boxplots summarize the distribution of numerical data using quartiles, displaying the median, interquartile range, and outliers. They provide insights into the spread and skewness of data, making them essential for understanding data variability and identifying outliers in a compact visual format.

## Histograms

Histograms introduce a new idea, **probability distributions**, into the discussion.
A probability distribution is simply a table listing the probability that a variable will have a particular value.

In our work, you can think in terms of **count distributions** or the number of times a variable has a particular value.
We will use the term **distribution** to refer to either count or probability distributions interchangeably.

There are as many different types of distributions - as many as different types of animals in the zoo!
For our purposes, we highlight five general shapes of distributions:

- **Uniform:** a flat distribution where every value is equally likely
- **Normal:** a bell curve distribution where values toward the middle are most likely
- **Skewed right:** a declining distribution were small values are likely and large values unlikely
- **Skewed left:** the opposite of skewed right
- **Mixtures:** appear as two or more of the above distributions

The purpose of generating histograms is to visually determine the approximate distribution of a variable.
Histograms can reveal extreme values, missing ranges, or skew, that may require special care in later analysis.

Histograms:

- Require x
- Automatically determine bar widths for x
- Automatically define y as the count of values for x
- Are used to show the distribution of a **single** variable

Let's look at a numeric example.

![](https://pbs.twimg.com/media/GQcgMq9WgAEltwX?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(dataframe,aes(MaxHR)) +
    geom_histogram()

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="ggplot_plus_R" id="mMp/iTi1[1}Zab[H4,uL" x="101" y="144"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="Hm;l4wO0?RC:sG~Gg4`f"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="Bd0hFnUIJ(fGQ-tHQ*9-"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="r3(,-xfsguvJgF`ORHZn"><field name="CODE">aes(MaxHR)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="3:YXAyd1-Di[h5Uh+;fS"><field name="CODE">geom_histogram()</field></block></value></block></xml>
```

# Boxplot

A boxplot, also known as a box-and-whisker plot, is a statistical visualization tool that provides a concise summary of the distribution of numerical data. The plot consists of a box that represents the interquartile range (IQR), spanning from the first quartile (Q1) to the third quartile (Q3). Inside the box, a line denotes the median (Q2) of the data. The whiskers extend from the box to the minimum and maximum values within a predefined range, typically 1.5 times the IQR. Outliers beyond this range are often plotted individually. Boxplots are valuable for identifying the spread, skewness, and potential outliers in datasets, offering insights into the variability and central tendency of the data in a clear and intuitive manner. They are widely used in exploratory data analysis and comparative studies across different groups or variables.

Let's try an example:

![](https://pbs.twimg.com/media/GQchEmwWUAAb0sq?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(dataframe,aes(y=MaxHR)) +
    geom_boxplot()

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="ggplot_plus_R" id="kS83jd+MZ4Oo55Qq/SU6" x="113" y="158"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="-J=o@WrP|MdLA|aAH109"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="w`@~#cUobt:C[r(XJL7s"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="Gb@uc^f7@L{M;Y}wGQ`h"><field name="CODE">aes(y=MaxHR)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="`ASSiVLbVLD1YKgnr(X2"><field name="CODE">geom_boxplot()</field></block></value></block></xml>
```


If want to breakdown your analysis having multiple boxplot by a categorical column:

![](https://pbs.twimg.com/media/GQchYxEXkAAK6Ok?format=jpg&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
ggplot2::ggplot(dataframe,aes(y=MaxHR,group=HeartDisease)) +
    geom_boxplot()

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable></variables><block type="ggplot_plus_R" id="fzqU`n7$h59.XN`{?99:" x="45" y="86"><mutation items="1"></mutation><value name="INPUT"><block type="varDoMethod_R" id="Ka;|DJ5iSw!7e1R3G,MP"><mutation items="2"></mutation><field name="VAR" id="dIuJSVx%Rw.Ne4=uLdpL">ggplot2</field><field name="MEMBER">ggplot</field><data>ggplot2:ggplot</data><value name="ADD0"><block type="variables_get" id="VD3ECof/XM,yCy}BN!%R"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value><value name="ADD1"><block type="dummyOutputCodeBlock_R" id="JQDi0B$*99JAT/_K7Y(f"><field name="CODE">aes(y=MaxHR,group=HeartDisease)</field></block></value></block></value><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="]t7KU}afN9^OU|JlP;fr"><field name="CODE">geom_boxplot()</field></block></value></block></xml>
```


You can see a summary of all commands with the [ggplot2 cheat sheet](https://github.com/rstudio/cheatsheets/blob/main/data-visualization.pdf)

# Predictive Analysis

Predictive analysis involves using historical data to make informed forecasts or predictions about future trends and outcomes. It encompasses various statistical and machine learning techniques aimed at understanding relationships between variables and leveraging these relationships to predict unknown or future values. Linear regression is a fundamental example of predictive analysis, particularly useful to infer a continuous dependent variables (label). It models the relationship between an independent variable (predictor) and a dependent variable (outcome) using a linear equation, allowing analysts to quantify the impact of changes in the predictor on the outcome. By fitting a line to the data points, linear regression provides insights into trends and patterns, helps in making predictions based on new data, and forms the basis for more complex predictive modeling techniques. Predictive analysis, including linear regression, finds applications across industries such as finance, marketing, healthcare, and beyond, aiding in decision-making and strategic planning based on data-driven insights.


## Linear Regression

Linear regression is a statistical method used to model the relationship between a dependent variable (often denoted as $Y$) and one or more independent variables (denoted as $X$. It assumes a linear relationship between the variables, where changes in the independent variables are associated with proportional changes in the dependent variable. The model takes the form of a linear equation,

$Y = \beta_0 + \beta_1 X + \epsilon$

where $\beta_0$ and $\beta_1$ are coefficients representing the intercept and slope of the line, respectively, and $\epsilon$ is the error term accounting for the variability in $Y$ that cannot be explained by the linear relationship with $X$.

In order to perform regressions, we are going to use the stats library do perform the training and the prediction. And the base library to report the summary of its statistical properties, as follow:
![base_stats](https://pbs.twimg.com/media/GXTw1vzXkAANXlf?format=png&name=240x240)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
library(base)
library(stats)

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="Hd74[//Z2em)0TbfSR./">base</variable><variable id="VC-h([vywA!*P.9Nw,4$">stats</variable></variables><block type="import_R" id="|03~waa~K=v4jZ+G`,V$" x="128" y="31"><field name="libraryName" id="Hd74[//Z2em)0TbfSR./">base</field><next><block type="import_R" id=")kV^WQ$vu$|~M;/!Ov[%"><field name="libraryName" id="VC-h([vywA!*P.9Nw,4$">stats</field></block></next></block></xml>
```

We can train the model with ***lm()*** function, that will be fitted to the function of Cholesterol based on RestingBP (*Cholesterol~RestingBP*).

Then the ***summary()*** function will provide detailed information about the regression model, including the coefficients, R-squared value, and p-values, which can help you interpret the strength and significance of the relationship.

![lm](https://pbs.twimg.com/media/GXfJlT_WgAAg7Vc?format=jpg&name=medium)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
model = stats::lm(Cholesterol~RestingBP,dataframe)
print(base::summary(model));

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="9u,igN5a-}#L2I8,SI1-">model</variable><variable id="VC-h([vywA!*P.9Nw,4$">stats</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable><variable id="Hd74[//Z2em)0TbfSR./">base</variable></variables><block type="variables_set" id="f-vqdE7c{^PYWVfPwk/^" x="31" y="54"><field name="VAR" id="9u,igN5a-}#L2I8,SI1-">model</field><value name="VALUE"><block type="varDoMethod_R" id="bN`r-]zj@GxhoKDRSKJ`"><mutation items="2"></mutation><field name="VAR" id="VC-h([vywA!*P.9Nw,4$">stats</field><field name="MEMBER">lm</field><data>stats:lm</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="!UQOjn0J,Df.WIClRmSt"><field name="CODE">Cholesterol~RestingBP</field></block></value><value name="ADD1"><block type="variables_get" id="+rMq2ZT|i%K^/y2V)(dH"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value></block></value><next><block type="text_print" id="4.5av`lxwkYEU#OO,%VD"><value name="TEXT"><shadow type="text" id=":]Q65rqhd$cW/DAWlC5-"><field name="TEXT">abc</field></shadow><block type="varDoMethod_R" id="[@4}^x1e9D^yqlB(bqH["><mutation items="1"></mutation><field name="VAR" id="Hd74[//Z2em)0TbfSR./">base</field><field name="MEMBER">summary</field><data>base:summary</data><value name="ADD0"><block type="variables_get" id="{In#lrWcAm|Kydr=iF1."><field name="VAR" id="9u,igN5a-}#L2I8,SI1-">model</field></block></value></block></value></block></next></block></xml>
```

We can then load the testing dataset. And with it execute the inferences using the ***predict()*** function.

![lm_pred](https://pbs.twimg.com/media/GXfKrWVWIAA4hYX?format=jpg&name=medium)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
test = readr::read_csv("heart - test.csv")
print(stats::predict(model,test));

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="|A4C3FfEKhK*xA!E_Tr|">test</variable><variable id="c}}IALaRyxW,6OvC9Na1">readr</variable><variable id="VC-h([vywA!*P.9Nw,4$">stats</variable><variable id="9u,igN5a-}#L2I8,SI1-">model</variable></variables><block type="variables_set" id="[/)Wd[A?f~OGc)V+}yzt" x="86" y="61"><field name="VAR" id="|A4C3FfEKhK*xA!E_Tr|">test</field><value name="VALUE"><block type="varDoMethod_R" id="QezoYh$Fe^Vuq939l@S)"><mutation items="1"></mutation><field name="VAR" id="c}}IALaRyxW,6OvC9Na1">readr</field><field name="MEMBER">read_csv</field><data>readr:read_csv</data><value name="ADD0"><block type="text" id="x~8sTF|x3`!%]{)k/5:A"><field name="TEXT">heart - test.csv</field></block></value></block></value><next><block type="text_print" id="5:8Ez[^SgTJQ,WxeozK]"><value name="TEXT"><shadow type="text" id="c2*sy0h9mTN}Soq*n^?i"><field name="TEXT">abc</field></shadow><block type="varDoMethod_R" id="}yJYb)l:gumG^~9I_]6^"><mutation items="2"></mutation><field name="VAR" id="VC-h([vywA!*P.9Nw,4$">stats</field><field name="MEMBER">predict</field><data>stats:predict</data><value name="ADD0"><block type="variables_get" id="qoQJclh7rQ`^ZDU7:.z7"><field name="VAR" id="9u,igN5a-}#L2I8,SI1-">model</field></block></value><value name="ADD1"><block type="variables_get" id="^rLWIA;R$o$LXIa0|Naf"><field name="VAR" id="|A4C3FfEKhK*xA!E_Tr|">test</field></block></value></block></value></block></next></block></xml>
```


## Classifier: Decision Tree

A decision tree classifier is a machine learning algorithm used for both classification and regression tasks. It works by recursively splitting the data into subsets based on the value of input features, creating a tree-like model of decisions. Each internal node of the tree represents a feature, each branch represents a decision rule, and each leaf node represents an outcome or class label. The goal is to create a model that predicts the target variable by learning simple decision rules inferred from the data features. Decision trees are popular due to their interpretability, simplicity, and ability to handle both numerical and categorical data.

For the decision tree, we going to use the **rpart** library, and its visual counter part, rpart.plot.

![](https://pbs.twimg.com/media/GQdtj7MW8AAIhct?format=png&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
library(rpart)
library(rpart.plot)
#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="[swZr*kYjos^+]$$l=Qr">rpart</variable><variable id="{:Gh^7_,:DbkQ(`2AEYb">rpart.plot</variable></variables><block type="import_R" id="QEHJWSZ5At[A$L?pJRs-" x="108" y="39"><field name="libraryName" id="[swZr*kYjos^+]$$l=Qr">rpart</field><next><block type="import_R" id="58m6g8tpas}PhE*7htox"><field name="libraryName" id="{:Gh^7_,:DbkQ(`2AEYb">rpart.plot</field></block></next></block></xml>
```

We can train the tree with the ***rpart()*** function of the hominimous library, *rpart::rpart()*, in which, we have HeartDisease as label (dependent variable) in function all the other independent variables (features).

![tree](https://pbs.twimg.com/media/GXfLAqQWQAEHwGe?format=png&name=900x900)

Not only we can do predictions with the trained tree, but we can interpret the rules that it uses perform the classification, as seen on the graphical representation of the tree below:


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
tree = rpart::rpart(HeartDisease ~ .,dataframe)
print(rpart.plot::prp(tree));

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="/hKc`T*#UM.*r-UsVj3n">tree</variable><variable id="[swZr*kYjos^+]$$l=Qr">rpart</variable><variable id="aqvv~Euo2xomJo:h4-_9">dataframe</variable><variable id="{:Gh^7_,:DbkQ(`2AEYb">rpart.plot</variable></variables><block type="variables_set" id="c{eKkLU82Qxoz5`pCvxJ" x="58" y="56"><field name="VAR" id="/hKc`T*#UM.*r-UsVj3n">tree</field><value name="VALUE"><block type="varDoMethod_R" id=",D]sXT4$+Tpe+iCu8%9Z"><mutation items="2"></mutation><field name="VAR" id="[swZr*kYjos^+]$$l=Qr">rpart</field><field name="MEMBER">rpart</field><data>rpart:rpart</data><value name="ADD0"><block type="dummyOutputCodeBlock_R" id="E[qKfoYa(S(0(Zcj$2/b"><field name="CODE">HeartDisease ~ .</field></block></value><value name="ADD1"><block type="variables_get" id="{8EUk(%eJdoHqsYbk.I1"><field name="VAR" id="aqvv~Euo2xomJo:h4-_9">dataframe</field></block></value></block></value><next><block type="text_print" id=",Mt:5g-%qe*td|eI/yXI"><value name="TEXT"><shadow type="text" id="3%E#Dc+KrTra+aHPBGGO"><field name="TEXT">abc</field></shadow><block type="varDoMethod_R" id="ffr:_fu,-Mw#K/o1X?eC"><mutation items="1"></mutation><field name="VAR" id="{:Gh^7_,:DbkQ(`2AEYb">rpart.plot</field><field name="MEMBER">prp</field><data>rpart.plot:prp</data><value name="ADD0"><block type="variables_get" id="cG6?s~0I3JM8y$W1B7n3"><field name="VAR" id="/hKc`T*#UM.*r-UsVj3n">tree</field></block></value></block></value></block></next></block></xml>
```


Lastly, we can perform the inferences with the ***predict()*** function.

![tree_pred](https://pbs.twimg.com/media/GXfLWFiXcAApSTu?format=png&name=small)


```R
# Click here to start your blocks coding

```

**Rubrics**: 
```
print(stats::predict(tree,test));

#<xml xmlns="https://developers.google.com/blockly/xml"><variables><variable id="VC-h([vywA!*P.9Nw,4$">stats</variable><variable id="/hKc`T*#UM.*r-UsVj3n">tree</variable><variable id="|A4C3FfEKhK*xA!E_Tr|">test</variable></variables><block type="text_print" id=",Z]Kc)v6/}YOMx(.mLQN" x="47" y="171"><value name="TEXT"><shadow type="text" id="d$klmql*Xj4Li=@J!]dI"><field name="TEXT">abc</field></shadow><block type="varDoMethod_R" id="^0{q1:(!U7:i$T^#(,]m"><mutation items="2"></mutation><field name="VAR" id="VC-h([vywA!*P.9Nw,4$">stats</field><field name="MEMBER">predict</field><data>stats:predict</data><value name="ADD0"><block type="variables_get" id="~50anf*]3-uaZl{)e,Mn"><field name="VAR" id="/hKc`T*#UM.*r-UsVj3n">tree</field></block></value><value name="ADD1"><block type="variables_get" id="ewS]ma*.9at)q=#EH-{^"><field name="VAR" id="|A4C3FfEKhK*xA!E_Tr|">test</field></block></value></block></value></block></xml>
```


# Explore More

- Feel free to explore more the dataset. Perform additional descriptive or statistical analysis.

# Next steps

If you enjoyed this workshop, the two options for next steps are:

- Our [full course](https://github.com/memphis-iis/datawhys-content-notebooks-r) on data science using R

