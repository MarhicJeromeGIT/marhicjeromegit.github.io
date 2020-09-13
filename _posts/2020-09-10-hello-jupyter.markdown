---
layout: post
title:  Displaying a Jupyter notebook in Jekyll
date: 2020-09-10 13:10:14 +0700
categories: notebooks
---

# Step by step

- Convert the notebook to markdown with jupyter nbconvert
  ```
  jupyter nbconvert --to markdown notebooks/2020/09/10/hello-jupyter.ipynb
  ```
- Copy the generated markdown in your /_posts article
- Note: Jekyll adds the content of the /notebook folder to the /_site folder data so the assets will be found automatically
if you set the post categories to 'notebooks'. No need to copy the assets folder.
  
Example : [Hello Jupyter notebook](hello-jupyter.ipynb)
```python
import matplotlib.pyplot as plt
```


```python
plt.plot([0,1,2],[0,1,4])
```




    [<matplotlib.lines.Line2D at 0x7fa537eba700>]




    
![svg](hello-jupyter_files/hello-jupyter_1_1.svg)
    



```python
print("hello jupyter")
```

    hello jupyter

