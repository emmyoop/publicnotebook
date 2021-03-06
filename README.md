# publicnotebook
Practice Repo to Demonstrate Publishing Jupyter Notebooks to static sites

- create repo in github
- create new conda environment
```conda create --n myenv```
```conda activate myenv```
- create notebook, install dependancies as needed, test!
- generate environment.yml - make sure not to get OS specific builds so don't include builds and only include what you specifically installed, not dependancies
 (https://github.com/jupyterhub/binder/issues/149)
```conda env export --no-builds --from-history > environment.yml```
- commit!

TODO: binder
- fill in page based on your repo https://mybinder.org/
- click launch
note: when you build with Binder the logs have a bunch of red output - it doesn't necesarily mean an error

- on success it will launch the familiar jupyter notebook homepage

- direct access at
- https://mybinder.org/v2/gh/<GitHub Username>/<repository name>/HEAD

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


