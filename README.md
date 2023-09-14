# [Spark Challenge](https://bootcampspot.instructure.com/courses/3337/assignments/54019?module_item_id=962092)

Glantz Adam Bootcamp RUT-VIRT-DATA-PT-04-2023-U-LOLC-MWTH - Module 22

**NOTE - The code must be run using** [Google Colab](https://colab.google/). **This is very important**

## TABLE OF CONTENTS

1. Overview
2. Summary
3. Installation
4. Contributing
5. Acknowledgements
6. Licenses

## 1. Overview:

In this challenge, SparkSQL was used to determine key metrics about home sales data. Spark was employed to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table had been uncached.

## 2. Results:

* The **purpose** of the [analysis](https://bootcampspot.instructure.com/courses/3337/assignments/54017?module_item_id=962033) is to create a tool for the nonprofit foundation Alphabet Soup that can help it select the applicants for funding with the best chance of success in their ventures.
* The **data** source is an [.csv](https://en.wikipedia.org/wiki/Comma-separated_values) file compiled by Alphabet Soup’s business team containing information on more than 34,000 organizations that have received funding from Alphabet Soup over the years.
* The **processes** are [machine learning](https://en.wikipedia.org/wiki/Machine_learning) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network), which are employed to construct a [binary classifier](https://en.wikipedia.org/wiki/Binary_classification) that can predict whether applicants will be successful if funded by Alphabet Soup.
* The **tools** of the project are [TensorFlow](https://en.wikipedia.org/wiki/TensorFlow), a free [open-source](https://en.wikipedia.org/wiki/Open-source_software) [library](https://en.wikipedia.org/wiki/Library_(computing)) with a particular focus on training and inference of deep neural networks, and [Keras](https://en.wikipedia.org/wiki/Keras), another open-source library that provides a [Python](https://www.python.org/) interface for TensorFlow. Coding was conducted in Python.
* **Success** is defined as creating a tool with a predictive power of 75% or more: i.e., its predictions are correct 75% of the time or more.

## 2. Results:

The business team's file contains the following metadata, each with a definition (**Figure 1**):

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/5ef4e180-6606-4ba9-b999-c3d343d8e359)

**Figure 1** | *Variable metadata with definitions*

**Data Preprocessing**

* What variable(s) are the target(s) for your model?

The target (i.e., [dependent](https://en.wikipedia.org/wiki/Dependent_and_independent_variables)) variable is `IS_SUCCESSFUL`, which contains the binary values `0` or `1`. As such, this task is one of classification.

* What variable(s) are the feature(s) for your model?

The features (i.e., independent variables) are all the remaining variables excluding `EID` (i.e., Employee Identification Number), discussed immediately below.

* What variable(s) should be removed from the input data because they are neither targets nor features?

Variables that were removed include `EID` and `NAME`, because these strings appear incidental to the performance and financial underpinnings of `IS_SUCCESSFUL`. _As I will demonstrate below, this is not the case_. `EID` is indeed expendable, but `NAME` is not.

**Compiling, Training, and Evaluating the Model**

* How many [neurons](https://en.wikipedia.org/wiki/Artificial_neuron), [layers](https://en.wikipedia.org/wiki/Layer_(deep_learning)), and [activation functions](https://en.wikipedia.org/wiki/Activation_function) did you select for your neural network model, and why?

I was able to confine the model to two hidden layers and an output layer (**Figure 2**). The hidden layers both used the [Rectified Linear Unit (ReLU)](https://builtin.com/machine-learning/relu-activation-function) activation function. Despite seeming simple, binary classification problems often involve complex, non-linear decision boundaries, perhaps like the subjective-sounding categories `USE_CASE` and `SPECIAL_CONSIDERATIONS`. ReLU introduces non-linearity to the model, enabling it to learn these non-linear relationships in the data. By contrast, my output layer used a [sigmoid](https://en.wikipedia.org/wiki/Sigmoid_function) activation function, since its results are confined to values of `0` and `1`, like the `IS_SUCCESSFUL` target variable. Finally, settling on the number of neurons was a trial-and-error process. I found that 80 neurons for the first hidden layer and 30 for the second worked well. The idea is that the earlier layers learn lower-level, more general features, while the later layers learn higher-level, more specific features. I therefore concentrated computational power with more neurons in the first layer, and then reduced the number in the second to capture the smaller number of high-level abstractions.

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/1162a3b7-07f1-431d-b509-6f670f84da1b)

**Figure 2** | *Allocation of neurons, layers, and activation functions in the model*

* Were you able to achieve the target model performance?

Yes, I was able to increase the accuracy of predictions on test data from 73.29% in my first attempt to 78.53% in my final (third) optimization (**Figure 3**). The final training result was 79.18%, only 0.65% percentage points higher than the final testing accuracy score, showing that overfitting was kept under control. As aforementioned, the benchmark for success is 75%, so this model could be of use to Alphabet Soup.

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/295d2cd4-b753-443f-9da9-dd5281d63fd9)

**Figure 3** | *Accuracy scores for training and test data in the last iteration of the model*

* What steps did you take in your attempts to increase model performance?

After my original attempt, I tried to improve accuracy by correcting what I saw as imperfections in the original setup: eliminating an additional column (`ORGANIZATION`) that appeared superfluous to the calculation of `IS_SUCCESSFUL`, and capturing more data in additional bins (**Figure 4** and **Figure 5**). This was unsuccessful: accuracy dropped from 73.29% to 72.78%.

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/d8da2ea4-495f-4795-93bc-0388030a2701)

**Figure 4** | _Code showing the dropping of additional field_ `ORGANIZATION` _in Optimization attempt 1_*

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/eaf6a8e6-a05f-4e35-9013-567eb316dea1)

**Figure 5** | _Example of increase in binning in Optimization attempt 1_*

I then decided to bring more computational power to bear on the problem by creating a third hidden layer with 20 neurons. This also didn't work, as accuracy fell to 72.45%. (**Figure 6**)

![image](https://github.com/aglantzrbc/deep-learning-challenge/assets/127694342/321a5fcf-ff4d-4eda-bcb4-27c1f8264fe8)

**Figure 6** | _Code showing the addition of another hidden layer in Optimization attempt 2_*

At that point, I interrogated the starter code and decided to keep the `NAME` variable in the analysis. This required binning name values, since I presume every name is unique. The change worked well and gave me the acceptable accuracy noted above.

**Summary:**

The successful increase in accuracy was only achieved after imprecise trial-and-error. There were four attempts, which involved dropping additional features, rebinning features, increasing the number of hidden layers, and finally retaining a feature that was previously dropped.

The results are surprising. The addition of the `NAME` variable makes a significant difference in accuracy. I would have thought that the only features with a bearing on `IS_SUCCESSFUL` are related to past behavior, sectoral position, and financial performance, with `NAME` merely an incidental string. That this is not the case raises several questions. First, do more efficient and financially responsible organizations use particular keywords in their names? Second, is there an inherent bias in the model that privileges particular names strings over others?  Investigating these lines of inquiry would require different [unsupervised machine learning](https://en.wikipedia.org/wiki/Unsupervised_learning) instrumentalities that are beyond the scope of this project.

Overall, another way to approach this classification task would be to try a different type of model, such as a [Random Forest Classifier](https://en.wikipedia.org/wiki/Random_forest) or a [Support Vector Machine (SVM)](https://en.wikipedia.org/wiki/Support_vector_machine). These models have been shown to be effective in binary classification problems and may be able to achieve a higher accuracy without the need for extensive optimization attempts. Additionally, they can handle both numerical and categorical variables and can handle outliers and imbalanced datasets well, which may be present in this dataset. Therefore, it may be worth exploring these alternative models as a potential solution to the classification problem.

## 3. Installation:

- The [GitHub](https://github.com/aglantzrbc/deep-learning-challenge) repository (version 2.9.1) containing all project files is publicly accessible.
- **Constituent program files and their locations:**
  -  _Jupyter_Notebook_Files_ - Subfolder contains the _Original_ attempt file and three subsequent _Optimization_ files, in sequence, all with an .ipynb extension.
  -  _H5_Files_ - Subfolder containing the same files, each with an .h5 extension.
- Since h5 files have already been created, the last cell of each .ipnyb file should not be rerun.
- The assignment details and starter code are proprietary and located on the [Rutgers University](https://www.rutgers.edu/) [(edX)](https://www.edx.org/) Bootcamp Spot [Module 22 Challenge](https://bootcampspot.instructure.com/courses/3337/assignments/54019?module_item_id=962092) webpage.
- This project was created on a [PC](https://en.wikipedia.org/wiki/Personal_computer) using [Google Chrome](https://www.google.com/chrome/) for [Windows](https://www.microsoft.com/en-us/windows) version 115.0.5790.102 and its associated [Google DevTools](https://developer.chrome.com/docs/devtools/) extension. **If the program doesn't function, it is recommended that the user attempt running it on this platform and browser.**
- Coding was guided by the [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) ("don't repeat yourself") principle.

## 4. Contributing:

- [Glantz, Adam](https://www.linkedin.com/in/adam-glantz/): Annapolis, Maryland, USA, September 2023, email: adamglantz@yahoo.com

## 5. Acknowledgements:

In addition to using the resources listed above, the author acquired query responses in OpenAI's [ChatGPT](https://chat.openai.com/) versions 3.5 and 4 apps, and the [VSCode GitHub Copilot](https://github.com/features/copilot) app V1.

The author also consulted code and results from similar projects publicly accessible in [GitHub](https://github.com/) repositories and recoverable through [Google](https://www.google.com/) and comparable search engines:

- [briansmlee](https://stackoverflow.com/users/20086392/brianmslee): April 2023. [Home-Sales-Big-Data-with-PySpark-SQL](https://github.com/brianmslee/Home-Sales-Big-Data-with-PySpark-SQL)
- [Heidari, Ali T.](https://www.linkedin.com/in/theidari/): Toronto, Ontario, Canada, April 2023. [home_sales](https://github.com/theidari/home_sales)
- [Sultani, Farrukh](https://www.linkedin.com/in/farrukh-sultani-b5583060/): California, USA, May 2023. [Home_Sales](https://github.com/FarrukhSultani/Home_Sales)

## 6. Licenses:

- This program is allowed for free use via the [Creative Commons Zero v1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) license
