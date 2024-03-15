# jupyter

## install
```
conda install -y -c conda-forge jupyter nb_conda jupyter_contrib_nbextensions
conda clean --all
```

## jupyter_notebook_config.py
```
c.NotebookApp.ip='*'
c.NotebookApp.password = ''
c.NotebookApp.open_browser = False 
c.NotebookApp.port = 8888
```

## start service
```
jupyter notebook --allow-root --notebook-dir=/data > /data/jupyter.log 2>&1 &
```

## build docker
```
FROM irepoing/python:conda
RUN conda install -y -c conda-forge jupyter nb_conda jupyter_contrib_nbextensions \
    && conda clean --all \
    && jupyter notebook --generate-config -y

COPY jupyter_notebook_config.py /root/.jupyter/jupyter_notebook_config.py

ENTRYPOINT ["jupyter", "notebook --allow-root"]
```