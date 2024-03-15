# pip

## src install
```
python setup.py install
```

## update specify version
```
pip install --upgrade pip==10.0.0
python -m pip install --upgrade pip==10.0.0
```

## install specify version
```
pip install "requests==2.5" 
pip install "requests>=2.0" 
pip install "requests<=3.0"
pip install "requests>=2.0,<=3.0"
```

## temp index url
```
pip install -i http://mirrors.aliyun.com/pypi/simple --trusted-host mirrors.aliyun.com --no-cache-dir numpy
```

## get index url
```
pip config get global.index-url
```

## set index url
```
pip config set global.index-url http://mirrors.aliyun.com/pypi/simple
pip config set install.trusted-host mirrors.aliyun.com
```

## export install package
```
pip freeze > requirements.txt
pip freeze --all > requirements.txt
```

## dowload package to dir
```
pip download xxx  -d /paks
pip download -r requirements.txt  -d /packs
```

## install package from dir
```
pip install -d /packs -r requirements.txt
pip install --no-index --find-links=/packs xxx
pip install --no-index -f /packs -r requirements.txt
```

## list expire package
```
pip list --outdate
```

## download package and install from lan
```
pip config set download.trusted-host mirrors.aliyun.com
pip download --trusted-host mirrors.aliyun.com -r requirements.txt -d /packs
pip install --no-index -f file://xxx/packs numpy
```

## packing source wheel
```
pip wheel --wheel-dir=/dst /src
```

## clean pip cache
```
pip cache purge
```