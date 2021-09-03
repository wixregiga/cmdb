<h1 align="center">CMDB</h1>
<div align="center">

As far as possible to achieve more universal configuration and management of IT resources
</div>

<div align="center">

[![License](https://img.shields.io/badge/License-GPLv2-brightgreen)](https://github.com/pycook/cmdb/blob/master/LICENSE)
[![UI](https://img.shields.io/badge/UI-Ant%20Design%20Pro%20Vue-brightgreen)](https://github.com/sendya/ant-design-pro-vue) 
[![API](https://img.shields.io/badge/API-Flask-brightgreen)](https://github.com/pallets/flask) 

</div>


[中文](README.md) / [English](README_en.md)

## DEMO ONLINE
- Preview online: [CMDB](http://121.42.12.46:8000)
    - username: demo
    - password: 123456
    
> **ATTENTION**: branch `master` may be unstable as the result of continued development, please pull code from  [releases](https://github.com/pycook/cmdb/releases)

----
## Overview
### Documents
- [Design document](https://zhuanlan.zhihu.com/p/98453732)
- [API document](https://github.com/pycook/cmdb/tree/master/docs)
- [Tree view practice](https://mp.weixin.qq.com/s/EflmmJ-qdUkddTx2hRt3pA)

The CMDB is a universal project that can define and manage almost all IT resources, even every resource as long as you want to, which treat all IT resources as resource objects. Objects has both attributes  and relationship.

CMDB's main distinguishing features as compared to other resource systems are:
- Define attributes of resource objects dynamically，you don't need to define all the attributes at the beginning.
- Define relationship of resource objects dynamically and simply, even you can draw the relationship through the web.
- Three view:
    - Resource view: model instance data that users can subscribe
    - Tree view: the model is hierarchical by field, shown in a tree diagram, and users can subscribe
    - Relational view: relationships between models, shown in a tree diagram, **are configurable by the administrator**

- Authority management


## Install

There are various ways of installing CMDB.

### Install by Docker
- Prepare: install docker and docker-compose
- In directory cmdb
    ```
        docker-compose up -d
    ```
- View: [http://127.0.0.1:8000](http://127.0.0.1:8000)

### Environment and dependency
- database: mysql
- cache: redis
- python: python2.7, >=python3.6

### Install
- Start mysql, redis
- Create mysql database: cmdb
- Pull code
    ```bash
    git clone https://github.com/pycook/cmdb.git
    cd cmdb
    cp cmdb-api/settings.py.example cmdb-api/settings.py
    ```
    **set database in config file cmdb-api/settings.py**

- Install library
  - backend: ```cd cmdb-api && pipenv run pipenv install && cd ..```
  - frontend: ```cd cmdb-ui && yarn install && cd ..```
  
- Create tables of cmdb database:
    
  in **cmdb-api** directory: ```pipenv run flask db-setup && pipenv run flask init-cache```
- Suggest step: (default:  user:demo,password:123456)

    ``` source docs/cmdb.sql```

- Start service
  - backend: in **cmdb-api** directory: ```pipenv run flask run -h 0.0.0.0```
  - frontend: in **cmdb-ui** directory: ```yarn run serve```
  - worker: in **cmdb-api** directory: ```pipenv run celery worker -A celery_worker.celery -E -Q cmdb_async --concurrency=1```
  
  - homepage:  [http://127.0.0.1:8000](http://127.0.0.1:8000)
    - if not run localhost: please change ip address(**VUE_APP_API_BASE_URL**) in config file **cmdb-ui/.env** into your backend ip address

### Install by Makefile
- Start mysql,redis
- Create mysql database: cmdb
- Pull code
    ```bash
    git clone https://github.com/pycook/cmdb.git
    cd cmdb
    cp cmdb-api/settings.py.example cmdb-api/settings.py
    ```
    **set database in config file cmdb-api/settings.py**

- In cmdb directory,start in order as follows:
    - enviroment: ```make env```
    - start API: ```make api```
    - start UI: ```make ui```
    - start worker: ```make worker```
    
## Contributing

1. Fork it
1. Create your feature branch (`git checkout -b my-feature`)
1. Commit your changes (`git commit -am 'Add some feature'`)
1. Push to the branch (`git push origin my-feature`)
1. Create new Pull Request


## DEMO
##### resource view
![resource view](https://raw.githubusercontent.com/pycook/cmdb/master/cmdb-ui/public/cmdb-ci.jpeg) 

##### tree view
![tree view](https://raw.githubusercontent.com/pycook/cmdb/master/cmdb-ui/public/cmdb-tree.jpeg) 

##### relationship view
![relationship view](https://raw.githubusercontent.com/pycook/cmdb/master/cmdb-ui/public/cmdb-relation.jpeg) 

##### user subscription
![user subscription](https://raw.githubusercontent.com/pycook/cmdb/master/cmdb-ui/public/cmdb-preference.jpeg)

##### define relationship view
![define relationship view](https://raw.githubusercontent.com/pycook/cmdb/master/cmdb-ui/public/cmdb-relation-define.jpeg)

-----
_**Welcome to join us through QQ group（336164978）**_

![QQgroup](cmdb-ui/public/qr_code.jpg)
