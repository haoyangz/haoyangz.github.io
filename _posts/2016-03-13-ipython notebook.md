---
layout: post
title: Notes on Ipython Notebook
---
#### Project management
Let's look at what notebook is good at:

+	Visualize results (not preprocessing) 
+	Document high-levle procedure (not details) to make sure reproducibility

And notebook becomes a pain when:

+	too long (too many codes / figures / analyses) to navigate around
+ 	several analyses with similar procedures but different parameters co-exist (they will share the variable space and step on each other)
+  some cell takes a long time to finish

Therefore, some rules of thumb for reasonabily use notebooks for a research project:

+	Put different analyses in separate notebooks. Even when the results from different analyses need be aggregated, use an additional "figure generation" or "summary" notebook rather than putting everything into one notebook.
+	Consider putting code in actual files and call them from the notebook when this part of code:
	+ takes long time to finish (e.g, training)
	+ will be repeatedly used by different cells / analyses
+	Name the notebooks and organize the folder structure in meaningful ways. Optionally document with README in markdown
+ 	Write functionals that will be universally useful (e.g, plotting precision-recall curve) across different projects into a "helper" class, and call it in every notebook by the following so that it will automatically reload the function when it changes:


	```
	import sys
	sys.path.insert($the_path_of_your_helper_class)
	%reload_ext autoreload
	%autoreload 2
	%aimport $your_helper_class
	```

#### Execute shell command
Instead of calling "os.system" which hides the call back of the command, the clean way should be:

```
cmd = 'ls -lrt'  ## The shell command you wish to execute
callback = ! $cmd

## Or simply
callback = ! ls -lrt

## If the command is to run another python script
$cmd = 'anotherscript.py arg1 arg2'
callback = %run $cmd 
``` 
#### Logging
When running some block of code that takes a long time, we wish to redirect the log to a file. This preserves the full log even if we close the notebook before the code finishes. The clean way to do this is still under investigation.

#### Table display
Two clean and concise ways to checkout the data in your table:

```
from IPython.display import display

## The panda table you wish to visualize
table = pandas.DataFrame(mat,columns=['col1','col2'])  

## This will show the beginning and the end of your table
display(table) 

## This will show the beginning of your table
table.head()   
```



