# jenkins


```shell
echo "PID Check..."

CURRENT_PID=$(ps -ef | grep java | grep prod-booking-batch* | awk '{print $2}')

echo "Running PID: {$CURRENT_PID}"

if [ -z $CURRENT_PID ] ; then
    echo "> Project is not running"
else
    echo "> kill -9 $CURRENT_PID"
    kill -9 $CURRENT_PID
   sleep 5
fi

echo "Deploy Project...."

nohup java -jar -DSpring.profiles.active=prod /home/nolbal-user/.jenkins/workspace/prod-booking-batch/build/libs/nolbal-booking-batch-0.0.1-SNAPSHOT.jar &

echo "Done"
```


### dev
```shell
echo "PID Check..."

CURRENT_PID=$(ps -ef | grep java | grep dev-booking-batch* | awk '{print $2}')

echo "Running PID: {$CURRENT_PID}"

if [ -z $CURRENT_PID ] ; then
    echo "> Project is not running"
else
    echo "> kill -9 $CURRENT_PID"
    kill -9 $CURRENT_PID
   sleep 5
fi

echo "Deploy Project...."

nohup java -jar -DSpring.profiles.active=dev -Djasypt.encryptor.password=STAYNobaljk12345zxcvECXStDev0987 /home/nolbal-user/.jenkins/workspace/dev-booking-batch/build/libs/nolbal-booking-batch-*.jar &

echo "Done"
```
