# Домашнее задание к занятию "`8.2. Что такое DevOps. СI/СD`" - `Соловьев Денис`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

`Приведите ответ в свободной форме........`

1. https://github.com/dsolovev455/8-02/blob/main/txt/1.txt

/usr/local/go/bin/go test .
docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER
docker login ubuntu-bionic:8082 -u admin -p 123 && docker push ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER && docker logout


![alt text](https://github.com/dsolovev455/8-02/blob/main/img/1.png)





---

### Задание 2

`Приведите ответ в свободной форме........`

1. https://github.com/dsolovev455/8-02/blob/main/txt/2.txt


pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/netology-code/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'docker login ubuntu-bionic:8082 -u admin -p 123 && docker push ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}

![alt text](https://github.com/dsolovev455/8-02/blob/main/img/2.png)


---

### Задание 3

`Приведите ответ в свободной форме........`

1. https://github.com/dsolovev455/8-02/blob/main/txt/3.txt
 

pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/netology-code/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'CGO_ENABLED=0 ; GOOS=linux ; /usr/local/go/bin/go build -a -installsuffix nocgo -o ~/mygoapp:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'curl -v -u admin:123 --upload-file ~/mygoapp:v$BUILD_NUMBER http://ubuntu-bionic:8081/repository/raw/mygoapp:v$BUILD_NUMBER' }
    
  }
 }
}


![alt text](https://github.com/dsolovev455/8-02/blob/main/img/3.png)






### Задание 4

`Приведите ответ в свободной форме........`

1. Версионирование было добавлено ещё в 3-м задании
