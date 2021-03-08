# publicnotebook
Practice Repo to Demonstrate Publishing Jupyter Notebooks to static sites

- create repo in github
- create new conda environment
```conda create --n myenv```
```conda activate myenv```
- create notebook, install dependancies as needed, test!
- for extra fun make it interactive with ipywidgets (https://www.nbinteract.com/tutorial/tutorial_interact.html)
- generate environment.yml - make sure not to get OS specific builds so don't include builds and only include what you specifically installed, not dependancies
 (https://github.com/jupyterhub/binder/issues/149)
```conda env export --no-builds --from-history > environment.yml```
- manually add nbinteract (or any other pip installs)
```
  - pip:
      - nbinteract
```

- commit!

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


