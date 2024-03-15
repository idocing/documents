# conda

## use channels
```
conda install -c https://mirrors.aliyun.com/anaconda/pkgs/free numpy
```

## add channels
```
conda config --add channels https://mirrors.aliyun.com/anaconda/pkgs/free
```

## clean cache
```
conda clean --all
```

## docker image
```
FROM irepoing/debian:base

WORKDIR /root

COPY Miniconda.sh Miniconda.sh

RUN bash Miniconda.sh -b -p /opt/miniconda \
    && /opt/miniconda/bin/conda init \
    && /opt/miniconda/bin/conda clean --all \
    && bash && rm Miniconda.sh

ENV PATH=$PATH:/opt/miniconda/bin
```