-- create images
>cd M:\Docker\oracle
>mkdir data
[bash]
#cd cd M:\Docker\oracle
#git clone https://github.com/oracle/docker-images.git
#cd M:\Docker\oracle\docker-images\OracleDatabase\SingleInstance\dockerfiles
#./buildContainerImage.sh -v 21.3.0 -x
-- create container
[cmd]
>docker run --name oracle21xe -p 1522:1521 -p 5501:5500 -e ORACLE_PWD=oracle -v M:\Docker\oracle\data:/opt/oracle/oradata oracle/database:21.3.0-xe
-- connect to container
> docker exec -it oracle21xe /bin/bash
[cmd]
-- enable oracle manager
> docker exec -it oracle21xe /bin/bash
# sqlplus "/as sysdba"
sql> exec dbms_xdb.setlistenerlocalaccess(false);
-- open browser
https://localhost:5501/em/login
sys
oracle
xepdb1


-- connect to db
> sqlplus system/oracle@oracle21xe