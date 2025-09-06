# DevOps 

### Docker Documentation


```
docker login -u           mimaraslan    -p          123456789

docker login --username   mimaraslan    --password  123456789

docker login -u           mimaraslan    --password  123456789

```

```
docker run    --name   my-postgres   -e POSTGRES_USER=postgres    -e POSTGRES_PASSWORD=123456789   -e POSTGRES_DB=postgres  -p 9999:5432    -d postgres
```


### ===============  kendi jarlarımızı image olarak docker'a verme  ====================== 

```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.1.jar      --tag mimaraslan/devops-01-hello:v001   .
```

```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.1.jar      --tag mimaraslan/devops-01-hello:latest   .
```


```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.2.jar      --tag mimaraslan/devops-01-hello:v002   .
```

```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.2.jar      --tag mimaraslan/devops-01-hello:latest   .
```


```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.3.jar      --tag mimaraslan/devops-01-hello:v003   .
```

```
docker build    --build-arg   JAR_FILE=target/devops-01-hello-1.0.3.jar      --tag mimaraslan/devops-01-hello:latest   .
```



### ===============  kendi imagelerimizi container olarak çalıştırma ====================== 


```
docker           run       -it     -d           --name my-app1         -p 8081:8080                      mimaraslan/devops-01-hello:v001
```

```
docker container run       -it     -d           --name my-app1         -p 8081:8080                      mimaraslan/devops-01-hello:v001
```

```
docker  run       -it     -d           --name my-app2         -p 8082:8080                      mimaraslan/devops-01-hello:v002
```

```
docker  run       -it     -d           --name my-app3         -p 8083:8080                      mimaraslan/devops-01-hello:latest
```

```
docker  run       -it     -d           --name my-app4         -p 8084:8080                      mimaraslan/devops-01-hello
```


http://localhost:8081 </br>
http://localhost:8082 </br>
http://localhost:8083 </br>
http://localhost:8084 </br>


### ===============  kendi imagelerimizi dockerhub'a gönderme  ======================
```
docker push mimaraslan/devops-01-hello:v001
docker push mimaraslan/devops-01-hello:v002
docker push mimaraslan/devops-01-hello:latest
docker push mimaraslan/devops-01-hello
```

### ===============  kendi imagelerimizi dockerhub'dan çekme  ======================
```
docker pull mimaraslan/devops-01-hello:v001
docker pull mimaraslan/devops-01-hello:v002
docker pull mimaraslan/devops-01-hello:latest
docker pull mimaraslan/devops-01-hello
```



### ============== network ==============
### networkleri listele

```
docker network ls
```

### yeni bir network oluştur
```
docker network create my-network
```

### network tipini değiştirmek istiyorsanız --driver parametresi
```
docker network create --driver bridge my-network
```


### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```


### networke container ekleme
```
docker network connect my-network my-app1
docker network connect my-network my-app2
docker network connect my-network my-app3
```

### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```

### networke container çıkarma
```
docker network disconnect my-app2
```


### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```

### networkü silme
```
docker network rm my-network
```


### ============== volume ==============
```
docker volume ls
```
### Yeni bir volume oluşturmak
```
docker volume create my-volume
```

```
docker volume ls
```

```
docker volume inspect my-volume
```

### bir volume silmek
```
docker volume rm my-volume
```

### kullanılmayan tüm volumeleri silmek
```
docker volume prune
```

### ============= docker-compose ===================
```
docker compose -f docker-compose.yml up

docker compose -f docker-compose.yaml up
```

```
docker ps
```

```
docker container ls
```

```
docker-compose logs mongo
docker-compose logs -f  mongo
```


```
docker compose -f docker-compose.yml down

docker compose -f docker-compose.yaml down
```





### ============== Kubernetes K8s ===========


https://kubernetes.io/docs/concepts/overview/components/

https://minikube.sigs.k8s.io/docs/start/

Windows için minikube kurulum komudu
```
winget install Kubernetes.minikube
```

MacOS için minikube kurulum komutu
```
brew install minikube
```

== Yeni bir terminal aç ve işin bitinceye kadar onu açık tut ===
```
minikube start
```
== Yeni bir terminal aç ve işin bitinceye kadar onu açık tut ===
```
minikube dashboard
```

```
docker pull   mimaraslan/devops-01-hello:latest
```

```
docker  run     --name my-app1     -p 8081:8080    -it   -d       mimaraslan/devops-01-hello:latest
```


```
kubectl version
```








```
kubectl run    my-pod1    --image=mimaraslan/devops-01-hello:latest
kubectl run    my-pod2    --image=mimaraslan/devops-01-hello:v002
kubectl run    my-pod3    --image=mimaraslan/devops-01-hello:v003

kubectl get pods


kubectl run    my-pod4    --image=mimaraslan/devops-01-hello:v004

kubectl get pods


kubectl delete -n default pod my-pod4

kubectl get pods



kubectl run    my-pod4    --image=mimaraslan/devops-01-hello:v004

kubectl get pods



kubectl run    my-pod5    --image=mimaraslan/devops-01-hello:v001
kubectl run    my-pod6    --image=mimaraslan/devops-01-hello:v002
kubectl run    my-pod7    --image=mimaraslan/devops-01-hello:v003





kubectl run    my-pod8    --image=mysql

kubectl delete pod my-pod8

kubectl get pods


kubectl get pods   
kubectl get pod
kubectl get po

kubectl get pods   -o wide
kubectl get pod   -o wide
kubectl get po   -o wide




kubectl get nodes   
kubectl get node
kubectl get no

kubectl get nodes   -o wide
kubectl get node   -o wide
kubectl get no   -o wide
```

===   pod ===
```

kubectl apply -f    _01_my_pod_create.yaml

kubectl get pods  -o wide

kubectl delete pod    devops-01-hello

kubectl get pods

```

===   deployment ===


```
kubectl apply -f   _01_my_deployment_create.yaml

kubectl delete deployment devops-01-hello


kubectl get deployment

kubectl get deploy

kubectl get deployment  -o wide

kubectl get deploy  -o wide
```

===   service  ===
```

kubectl apply -f   _01_my_service_create.yaml

kubectl delete service devops-01-hello


kubectl get services  -o wide

kubectl get service  -o wide

kubectl get svc  -o wide

```

== İşin bitinceye minikube'ü durur ve terminali kapat. ===
```
minikube stop
```

![DevOps 1 - Docker.png](my-docs/DevOps%201%20-%20Docker.png)

![DevOps 2 - Docker.png](my-docs/DevOps%202%20-%20Docker.png)


<hr>

### Ödevinizin cevabı

#### 1. Adım:
   yaml dosyalarında tüm portları 8080 yapın.


#### 2. Adım
   Deployment dosyasını çalıştırın.
```
kubectl apply -f   _01_my_deployment_create.yaml
```


#### 3. Adım
   Service dosyasını çalıştırın.
```
kubectl apply -f   _01_my_service_create.yaml
```

4. Adım aşağıdaki komutu çalıştırın. Otomatik olarak bir port verilecek ve uygulama K8s üzerinde çalıştırılacak.

minikube service    SERVISE_VERDIGINIZ_AD  
```
minikube service    devops-01-hello     
```


Buradaki port otomatik verildi.
![DevOps 3- Service Run.png](my-docs/DevOps%203-%20Service%20Run.png)

![DevOps 4- App Work.png](my-docs/DevOps%204-%20App%20Work.png)

<hr>

İlle de 9090'dan çalıştırmak için service dosyasında dış port ile type kısmını değiştireceğiz.

1. Adım:

![DevOps 5 - localhost 9090.png](my-docs/DevOps%205%20-%20localhost%209090.png)


#### 2. Adım
Deployment dosyasını yeniden çalıştırın.
```
kubectl apply -f   _01_my_deployment_create.yaml
```


#### 3. Adım
Service dosyasını yeniden çalıştırın.
```
kubectl apply -f   _01_my_service_create.yaml
```


4. Adım aşağıdaki komutu çalıştırın. Localde port artık  9090 olacak.

```
kubectl port-forward service/devops-01-hello 9090:9090 
```

![DevOps 6 - App Work 9090.png](my-docs/DevOps%206%20-%20App%20Work%209090.png)


# DevOps Pipeline

## CI/CD Evreni

```

CI/CD:           (Jenkins, Git,  GitHub, GitOps,  GitHub Actions,    GitLab, GitLab CI,    Bitbucket, Bamboo)
Scripting        (Python, Bash, PowerShell)
Containers:      (Docker)
Orchestration:   (Kubernetes, Helm)
Cloud            (AWS, Azure, GCP)
Virtualization:  (VMware, VirtualBox)
IaC:             (Terraform, Ansible, CloudFormation)
Monitoring:      (Prometheus, Grafana, ELK)
```

<hr>

### Jenkins enregrasyon aşamaları
```
Kod ---> GitHub    --->  Jenkins      --->  DockerHub  --->  Kubernetes
         GitLab           -Git              -image            -container   
         Bitbucket        -Java
                          -Python
                          -C#
                          -Maven
                          -Gradle
                          -Docker
                          -Kubernetes
```

<hr>

### Jenkins'i indirmek
https://www.jenkins.io/download/


### Jenkins'i war dosyasından çalıştırmak
https://www.jenkins.io/doc/book/installing/war-file/

```
cd D:\DevOps

java -jar jenkins.war --httpPort=9999
```

<hr>

###  Docker'a Terminalden Login olmak.
```
docker login -u           mimaraslan    -p          123456789

docker login --username   mimaraslan    --password  123456789

docker login -u           mimaraslan    --password  123456789

```



### Jar dosyasının Docker'a image olarak göndermek
```
docker build    --build-arg   JAR_FILE=target/devops-application.jar      --tag mimaraslan/devops-application:latest   .

docker build    --build-arg   JAR_FILE=target/devops-application.jar      -t mimaraslan/devops-application:latest   .

docker build    --tag mimaraslan/devops-application:latest   .

docker build  -t mimaraslan/devops-application:latest   .
```

<hr>

### GitHub Token for DevOps
https://github.com/settings/tokens/new

### DockerHub Token for DevOps
https://app.docker.com/accounts/mimaraslan/settings/personal-access-tokens




###  DockerHub Token ile Terminalden login olmak
```
docker login -u mimaraslan     -p   dckr_pat_y9zp_9RxQEsjw-0DoInBz6_abc
```

### DockerHub Token ile Jenkins'ten login olmak
```
docker login -u mimaraslan     -p   ${DOCKER_HUB_TOKEN}

```

<hr>

### Docker Image'ını DockerHub'a göndermek
```
docker push mimaraslan/devops-application:latest
```

<hr>

### Windows'ta minikube config dosyasının konumu
```
C:\Users\YOUR_USERNAME\.kube\config
```

### MacOS'ta minikube config dosyasının konumu
```
~/.kube/config
```

### minikube
```
minikube start

minikube dashboard

minikube service devops-application-service
```


# DevOps Pipeline

## CI/CD Evreni

```

CI/CD:           (Jenkins, Git,  GitHub, GitOps,  GitHub Actions,    GitLab, GitLab CI,    Bitbucket, Bamboo)
Scripting        (Python, Bash, PowerShell)
Containers:      (Docker)
Orchestration:   (Kubernetes, Helm)
Cloud            (AWS, Azure, GCP)
Virtualization:  (VMware, VirtualBox)
IaC:             (Terraform, Ansible, CloudFormation)
Monitoring:      (Prometheus, Grafana, ELK)
```

<hr>



AWS CLI kurulacak.
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

aws --version

MacOS

ls -la ~/
mv ~/Downloads/MyAWSKeyPair.pem ~/.ssh/
chmod 400 ~/.ssh/MyAWSKeyPair.pem
nano ~/.ssh/config

Host MyDevOpsAWS
HostName 54.204.235.127
User ubuntu
IdentityFile ~/.ssh/MyAWSKeyPair.pem

Ctrl + O
Enter
Ctrl + X

ssh MyAWSKeyPair


===My Jenkins Master ============================

Windows
MobaXterm üzerinden Session -> SSH oluşturacağız.


Terminalden bu 2 komutu sırayla çalıştıracağız.

sudo apt update

sudo apt upgrade  -y


===============================

İç IP adının yerine bir isim vereceğiz.
sudo nano /etc/hostname

isim olarak aşağıdakini yazdık.
My-Jenkins-Master

Ctrl + X'e bas.
Onaylamak için Y harfine bas.
En sonda da Enter'a bas.

veya

Ctrl + O'ya bas.
En sonda da Enter'a bas.



Makineyi yeniden başlat.

sudo init 6     ya da       sudo reboot

===============================

AWS EC2 makinemi dış dünyaya açtık.
Security groups kısmına gittik.
Dışarıdan 8080 portundan erişime izin verdik.

=======Java'yı kuracağız.========================

Terminale Java yaz ve enter'a bas. Açılan komutlardan birini al ve çalıştır.

sudo apt install openjdk-21-jre  -y

java --version


=======Jenkins'i kuracağız.========================

https://www.jenkins.io/doc/book/installing/linux/



sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian/jenkins.io-2023.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins  -y




Aşağıdaki komutları sırasıyla çalıştıracağız.
Bu makineyi Jenkins'e adıyoruz.
Makineyi kapatıp açtığımızda Jenkins otomatik olarak çalışır durumda olacak.

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins


Bu terminal'i kapatmadım sadece o durumdan çıktım. Terminalim açık.
Ctrl + C

Terminalime bu komutu yazıp Jenkins'in admin parolasını öğrendik.
sudo cat /var/lib/jenkins/secrets/initialAdminPassword




=== My Jenkins Agent ============================
Bu makine Docker'a özeldir.


Windows
MobaXterm üzerinden Session -> SSH oluşturacağız.


Terminalden bu 2 komutu sırayla çalıştıracağız.

sudo apt update

sudo apt upgrade  -y


===============================

İç IP adının yerine bir isim vereceğiz.
sudo nano /etc/hostname

isim olarak aşağıdakini yazdık.
My-Jenkins-Agent

Ctrl + X'e bas.
Onaylamak için Y harfine bas.
En sonda da Enter'a bas.


Makineyi yeniden başlat.

sudo init 6     
ya da       
sudo reboot



=======Java'yı kuracağız.========================

Terminale Java yaz ve enter'a bas. Açılan komutlardan birini al ve çalıştır.

sudo apt install openjdk-21-jre  -y

java --version

java -version




===== Docker kuracağız. ==========================

Terminale gelip sadece docker yaz ve enter'a.

sudo apt  install docker.io  -y

sudo usermod -aG docker $USER

sudo reboot



Makineleri birbirne tanıtacağız.
=== My Jenkins Master için ============================

sudo nano  /etc/ssh/sshd_config

Authentication kısmına gel.
Aşağıdaki şu iki satırın önündeki açıklama işaretini # kaldır.


# Authentication:

PubkeyAuthentication yes

AuthorizedKeysFile      .ssh/authorized_keys .ssh/authorized_keys2


Ctrl + X'e bas.
Onaylamak için Y harfine bas.
En sonda da Enter'a bas.

sudo service sshd reload


=== My Jenkins Agent için ============================

sudo nano  /etc/ssh/sshd_config

Authentication kısmına gel.
Aşağıdaki şu iki satırın önündeki açıklama işaretini # kaldır.


# Authentication:

PubkeyAuthentication yes

AuthorizedKeysFile      .ssh/authorized_keys .ssh/authorized_keys2


Ctrl + X'e bas.
Onaylamak için Y harfine bas.
En sonda da Enter'a bas.

sudo service sshd reload



=== My Jenkins Master için ============================

pwd

cd /home/ubuntu

SADECE İÇİN
Master makinenin takip edilebilmesi için bir şifre anahtar oluşturuyorum.

ssh-keygen


cd /home/ubuntu/.ssh/

ll


sudo cat  id_ed25519.pub


İçindeki böyle yazan satırı alıp kopyalayın.

ssh-ed25519 AAAAAAAAAAAAAAAAA ubuntu@My-Jenkins-Master



Sonuna kadar enter'a basıp geç.


=== My Jenkins Agent için ============================

cd /home/ubuntu/.ssh/

ll

sudo cat authorized_keys

Bu dosyanın için aç.
sudo nano authorized_keys

Master'dan aldığın şu satırı en alta yapıştır.
ssh-ed25519 AAAAAAAAAAAAAAAAA ubuntu@My-Jenkins-Master


==== Agent Takip eden taraf ===
ssh-rsa BBBBBBBBBBBBBBBBBB MyAWSKeyPair

==== Master'dan getirdiğim keygen anahtar takip edilecek taraf ===
ssh-ed25519 AAAAAAAAAAAAAAAAA ubuntu@My-Jenkins-Master


Ctrl + X'e bas.
Onaylamak için Y harfine bas.
En sonda da Enter'a bas.


cd /home/ubuntu/.ssh/

sudo cat authorized_keys


===================================
Master ve Agent makinelerini yeniden başlat.

sudo reboot



======================================
http://PUBLIC_IP:8080/computer/(built-in)/configure

Jenkins'i aç.
Nodes kısmına gel.

Built-In Node makinesinin içine gir.

Nodes -> Built-In Node -> Configure

Number of executors kısmını SIFIR 0 yap.





Agent makineyi Jenkins'e eklemek için
Nodes -> New node

http://PUBLIC_IP:8080/computer/new

Ona "My-Jenkins-Agent" diye bir isim verdik.
Permanent Agent olduğunu seçtik.


Jenkins'te Agent'ı eklerken onun kendi iç IP'sini alacaksın.


====== Master Makinedeki bu anahtarı okuyup kopyalayın ve Jenkins'e gelin. Credentials için ====

cd  /home/ubuntu/.ssh/

sudo cat id_ed25519


-----BEGIN OPENSSH PRIVATE KEY-----
CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC
-----END OPENSSH PRIVATE KEY-----


