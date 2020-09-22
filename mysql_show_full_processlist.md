```bash
#!/bin/bash
_current_time=$(date +%Y%m%d-%H%M)
_file_name="full_processl_list_${_current_time}"
MYSQL_PASS="xxx"
mysql -u root -p${MYSQL_PASS} -e "show full processlist;" > ${_file_name}
echo "


==========================================
==========================================
=============== LONG FORMAT  =============
==========================================
========================================== " >> ${_file_name}
mysql -u root -p${MYSQL_PASS} -e "show full processlist\G" >> ${_file_name}


# kill sleep mysql connection
_sleep_ids=$(mysql -u root -p${MYSQL_PASS} -e "select ID from information_schema.processlist where command = \"sleep\";";)

for _i in $_sleep_ids
do
        echo $_i
        mysql -u root -p${MYSQL_PASS} -e "kill ${_i}"
done
```
