# publicnotebook
Practice Repo to Demonstrate Publishing Jupyter Notebooks to static sites

- create repo in github
- create new conda environment
```conda create --n myenv```
```conda activate myenv```
- create notebook, install dependancies as needed, test!
- generate environment.yml - make sure not to get OS specific builds
 (https://github.com/jupyterhub/binder/issues/149)
```conda env export --no-builds --from-history > environment.yml```
- commit!

TODO: binder
note: when you build with Binder the logs have a bunch of red output - it doesn't necesarily mean an error

TODO: embed on page


