Learning is a funny thing.  Learning something with the purpose of teaching others is a funnier thing yet.  Generally, teaching others how to do something ot how something works increases your own knowledge of it.

I have a blog at [rockman.life](https://rockman.life) where I want to host my Jupyter Notebook Projects.  I would love those projects to be interactive when appropriate.  The problem is my website is a static site so having interactive content is more complex than it seems.

I decided to plunge into getting a notebook up on my blog, making it interactive and documenting the project along the way.  I have been thinking about it for a while and idle searching never found any *free* options that were easy to implement.

Finally I settled on using [Binder](https://mybinder.org) to host my notebook on their servers and [nbinteract](https://www.nbinteract.com/) to convert it to an html page I could embed in my own blog.  Here's how that works.

#### Create a Repository for your Project

I created a new public gihub project, [publicnotebook](https://github.com/emmyoop/publicnotebook).  

<image of project contents>


Once I created my simple notebook, I mvoed on to setting up my conda environment and getting everything installed.

```
conda create --n myenv
conda activate myenv

conda install pandas
```

Make sure you test everything out in your notebook and  you're happy with how it's all working go ahead and generate your enviroment file.  [Binder](https://mybinder.org) needs the enviroment file to create the Docker container your notebook will run on when you upload your project to their servers.  One thing to note is that you need to make sure not to get OS specific builds in your environment.yml so don't include builds and only include what you specifically installed, not any dependancies.  The best way to do that is via the following command.

```conda env export --no-builds --from-history > environment.yml```

We're also going to want to get [nbinteract](https://www.nbinteract.com/) installed but it is not available on conda.  You need to use pip to install it.  Then you'll want to manually add it to your environment.yml so it also ends up in the Docker container.  This is when you should add any other packages you installed with pip.

```
name: public-notebook-env
channels:
  - defaults
dependencies:
  - pandas
  - matplotlib
  - notebook
  - pip:
      - nbinteract
prefix: /Users/emily/anaconda3/envs/public-notebook-env
```


- add extnsion to initalize widget on load or it wont load properly - https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html#enabling-disabling-extensions  (not sure we want to do this - it broke me - trying to replicate)
```
conda install -c conda-forge jupyter_contrib_nbextensions

jupyter contrib nbextension install --user

jupyter nbextension enable init_cell/main
```
- commit!

- Still under investigation but I had to pip install nbinteract BEFORE all other packages I added via conda.  I could not get the right versions of everything otherwise.

TODO: binder
- fill in page based on your repo https://mybinder.org/
- click launch
note: when you build with Binder the logs have a bunch of red output - it doesn't necesarily mean an error

- on success it will launch the familiar jupyter notebook homepage.  wait until the itneractive version launches and play with it to make sure it all works as expected

- direct access at
- https://mybinder.org/v2/gh/<GitHub Username>/<repository name>/HEAD

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/emmyoop/publicnotebook/main?filepath=majors.ipynb)


TODO: embed on page
- install NBInteract
not available on conda, must pip install it
- navigate to directory holding the notebook file and run this to create an HTML file with the same name as the notebook
- need to specify the main instead of master branch since github no longer uses master branches - i subbited pulle request to fix this
```nbinteract majors.ipynb -s emmyoop/publicnotebook```
- modify the resulting HTML file
    - HTML5
    - reduce file size
    - only include the cells you want (kinda hacky)
    
- move html file into your blog
- I created a folder I will put all of them in.
```<iframe width="100%" height="50%" src="/embed_notebooks/majors-test.html"></iframe>```

todo: resize it better

resources:
https://elc.github.io/posts/embed-interactive-notebooks/
https://mybinder.org/
https://www.nbinteract.com/


