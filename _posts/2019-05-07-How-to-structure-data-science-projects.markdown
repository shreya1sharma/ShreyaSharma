---
layout: post
title:  "How to structure data science projects"
date:   2019-03-15 00:20:26 +0900
categories: 
---

Structuring a data science project is very important to logically proceed with data analysis, effectively share your findings with colleagues and easily reproduce your work. It saves a lot of time by removing confusion and improving data sharing. In this blog post, I summarize my strategy to structure a data science project. These lessons are learnt from my experience and from discussion with other data scientists.

## Steps 

**1. Create an appropriate folder structure**

* Make a separate folder for each project
* Keep logical folder names

Example folder structure:

	
	1. LICENSE
	2. README.md
	3. requirements.txt
	4. dataset
		4.1 raw  		
			4.1.1 train
			4.1.2 test
		4.2 processed   
		4.3 interim     
		4.4 external    -> data from external sources
		
	5. models           -> save the trained models and summary
	6. results          
	7. src              
		7.1 __init__.py -> Makes src a Python moduledata.py
		7.2 data        
			make_dataset.py
		7.3 features     
			build_features.py
		7.4 models       
			train.py
			predict.py
		7.5 visualization -> EDA, model and result visualization
			visualization.py
	8. notebooks -> for exploratory data analysis and explain the flow to others
	9. references -> papers, online blogs, articles etc.
	10. set_up.py -> to make the project pip installable
	
	
**2. Sketch the flow of data and code**

* create a diagram that shows the interaction of data and code before development
* discuss your code structure with a friend to check if it is easily understandable

Example diagram:

![image]({{site.url}}{{site.baseurl}}/assets/images/project_structure.jpg){:style="float:left;margin-left: 0px"}

**3. Modularize the code as much as possible**

* make three types of scripts -> general utility scripts, custom utility script for each type of functionality, main script to run the entire code
* create a separate code file for each functionality - data, model, visualization etc.
* Break the code into smaller pieces each intended to perform a specific task (may include sub tasks)
* Group these functions into modules (or python files) based on its usability. It also helps in staying organized and ease of code maintainability
* make separate file for general function and custom functions based on general functions
* use the *doc_string*ß* format when writing functions

**4. Make your code readable**

* Put all your imports, import x or library(x) at the top of your notebook. 
* Make sure to use white space and use it consistently. White space can serve like the breaks between paragraphs to help you group similar concepts together and help your readers follow the logical flow of the text.
* Break up long lines at logical places. For example, if you have a function that takes a lot of arguments, you can try inserting a line break after each argument.
* Make your variable names logical and human readable. 
* Comment your code! Especially for research code, when your intended audience may not be as fluent in your language of choice
* Use consistent patterns of capitalization. The prevailing pattern in data science tends to be lower_case_with_underscores for functions and variables, but as long as you’re consistent it doesn’t matter too much.

**5. Separate main files and analysis files**

* for research projects, create separate files for main code and analysis code
* try all the tests/functions on analysis code and after analysis append the useful ones in main code

**6. Save the environment information**

* Save the environment information so that others can easily reproduce your work in their machine and you can also port to a different setting

	   import IPython

	   # print system information (but not packages)
	   print(IPython.sys_info())

	   # get module information
	   !pip freeze > frozen-requirements.txt

	   # append system information to file
	   with open("frozen-requirements.txt", "a") as file:
    	   file.write(IPython.sys_info())

**7. Accessing and creating files**

* use relative rather than absolute file paths

		# read in data using absolute path
        data = pd.read_csv("/kaggle/input/WorldCupMatches.csv")

        # read in data using relative path
        data = pd.read_csv("../input/WorldCupMatches.csv")
* avoid the following when naming files- spaces, punctuation, accented characters, file names that don't tell anything about the content

**8. Controlling randomnness**

* set all the random number generators your code depends upon

![image]({{site.url}}{{site.baseurl}}/assets/images/seed.jpg){:style="float:left;margin-left: 0px"}

**7. Make an easy to understand ReadMe**

**8. Clean your project structure regularly**


**References**

1. [http://www.rctatman.com/files/Tatman_2018_ReproducibleML.pdf](http://www.rctatman.com/files/Tatman_2018_ReproducibleML.pdf)
2. [Reproducible research best practices](https://www.kaggle.com/rtatman/reproducible-research-best-practices-jupytercon?utm_medium=blog&utm_source=wordpress&utm_campaign=reproducibility-guide)
3. [Cookiecutter data science](https://drivendata.github.io/cookiecutter-data-science/)
4. [How to write production level code in data science](https://towardsdatascience.com/how-to-write-a-production-level-code-in-data-science-5d87bd75ced)
5. [Example directory structure](https://github.com/zhixuhao/unet)