
## Env file
Update env.sh file with your certified container's entitlement key and email address. The link to acquire the entitlement key is available in the env.sh file.

## Provision DB2, MQ and B2Bi

From this point forward, you must copy the commands from this README file and paste them into the terminal as directed.

## DB2
```
. env.sh ; ./deploy_db2.sh
```
```
oc logs -f ${DB2_NAME}-0
```
Wait until you see the following line in the log. Press Ctrl+c to break out of the log.
```
/database/config/db2inst1/sqllib/ctrl/db2strst.lck
```
```
./prepare_db2.sh
```
```
oc rsh pod/${DB2_NAME}-0 su - db2inst1
```
```
./db2reg.sh
```
```
db2 -stvf create_scc_db_b2bidb.sql
```
```
./db2-update.sh
```
```
exit
```

## MQ
```
./deploy_mq.sh
```

## B2Bi script
```
./deploy_b2bi.sh
```

## Check B2Bi's status
The ASI, AC, and API pods take 20 minutes to boot up. Before using auto-scalers, double-check that they are Ready 1/1.
```
oc get pods
```

## Auto scalers
```
envsubst < autoscalers.yaml | oc create -f -
```

## Log in to B2Bi
Retrieve B2Bi dashboard's URL. Log in with admin/password.
```
oc get route sterling-fg-b2bi-asi-internal-route -o jsonpath='{.spec.host} {"\n"}'
```

# Completion
You have now completed this lab successfully.


## Helm upgrade (when needed)
```
. env.sh
envsubst < ./ibm-b2bi-prod/values.yaml | helm upgrade b2bi ./ibm-b2bi-prod --namespace ${PROJECT_NAME} --values -
```

## Uninstall/Delete
```
envsubst < autoscalers.yaml | oc delete -f -
```

If needed, you may repeat this lab by uninstalling everything in reverse order.
```
delete_b2bi.sh
```
```
delete_mq.sh
```
```
delete_db2.sh
```
