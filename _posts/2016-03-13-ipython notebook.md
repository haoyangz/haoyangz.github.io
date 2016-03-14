---
layout: post
title: Notes on Ipython Notebook
---
#### Execute shell command
Instead of calling "os.system" which hides the call back of the command, the clean way should be:

```
cmd = 'ls -lrt'  ## The shell command you wish to execute
%run $cmd
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



