# [Spark Challenge](https://bootcampspot.instructure.com/courses/3337/assignments/54019?module_item_id=962092)

Glantz Adam Bootcamp RUT-VIRT-DATA-PT-04-2023-U-LOLC-MWTH - Module 22

**NOTE - The code must be run using** [Google Colab](https://colab.google/). **This is very important.**

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

**The following tasks were performed:**

* What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places. (See **Figure 1**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/778521bd-e4f9-43fe-ad69-ff217f1c7109)

**Figure 1** |

* What is the average price of a home for each year it was built that has three bedrooms and three bathrooms? Round off your answer to two decimal places. (See **Figure 2**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/6c02826f-be2d-418d-8724-900e7619dac7)

**Figure 2** |

* What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places. (See **Figure 3**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/9bc66f9d-0564-4774-9be4-0fee7c43e2e3)

**Figure 3** |

* What is the "view" rating for homes costing more than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places. (See **Figure 4**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/b4c3a23e-7714-4449-8a10-b8c0b34867a9)

**Figure 4** |

* What is the "view" rating for the same parameters using cached data? (See **Figure 5**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/25f77743-3806-42e4-8522-4479a20367ab)

**Figure 5** | *With cached data*

* What is the "view" rating for the same parameters using parquet data and how is its runtime different from cached data? (See **Figure 6**.)

![image](https://github.com/aglantzrbc/spark-challenge/assets/127694342/376a2aa7-b0cf-4102-8eb6-0723736c9e7e)

**Figure 6** | *With parquet data, and comparison*

## 3. Installation:

- The [GitHub](https://github.com/aglantzrbc/deep-learning-challeng) repository (version 2.9.1) containing all project files is publicly accessible.
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
