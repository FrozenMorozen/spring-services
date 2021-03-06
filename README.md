# spring-services

#### НАСТРОЙКИ

* В случае, если  предполагается использование kafka не из этого приложения, нужно изменить параметры сервера для consumer и producer.\
Для этого необходимо изменить параметры сервера kafka в следующих файлах:\
 `producer/src/main/resources/server.properties`\
 `consumer/src/main/resources/server.properties`

* Для kafka-server текущего приложения по умолчанию используется порт _9092_(для zookeeper: _2181_)\
  При необходимости отредактировать параметры `zookeeper-server` и `kafka-server1` в файле:\
  _kafka_docker_compose/docker-compose.yml_

* Для producer по умолчанию указан адрес: _localhost:8081_\
  При необходимости отредактировать настройку `server.port=8081` в файле:\
  _producer/src/main/resources/application.properties_
  
* Для consumer по умолчанию указан адрес: _localhost:8082_\
  При необходимости отредактировать настройку `server.port=8082` в файле:\
  _consumer/src/main/resources/application.properties_
___
#### ЗАПУСК ПРИЛОЖЕНИЯ
###### Все команды нужно выполнять из теущей директории (**/spring-services**)

**1.) Kafka-server**\
**`cd kafka_docker_compose/ && docker-compose up -d && cd ..`**

**2.) Producer**\
 В отдельной вкладке(или окне) терминала:\
**`cd producer && ./gradlew clean build && cd .. && java -jar producer/build/libs/producer-0.0.1-SNAPSHOT.jar`**

**3.) Consumer**\
 В отдельной вкладке(или окне) терминала:\
**`cd consumer && ./gradlew clean build && java -jar build/libs/consumer-0.0.1-SNAPSHOT.jar`**

___

#### ТЕСТИРОВАНИЕ

**`curl http://localhost:8081/test/94433b5a-31ab-469e-a80d-7f77d8445683`**

Логи для consumer см. в `consumer/logs/consumer.log`
___
#### ЗАВЕРШЕНИЕ РАБОТЫ

**`cd kafka_docker_compose/ && docker-compose stop && docker-compose rm -v -f && cd ..`**
