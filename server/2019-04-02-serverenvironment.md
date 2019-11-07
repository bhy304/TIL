# Tacotron Test at server 192.168.113.104

[Reference](https://github.com/srshin/blog/blob/master/python/2019-04-01-tacotron.md)

## Server 확인

* server
  * class26.encore.hrd 192.168.113.104 Ryzen 8core 32/49
* linux version 확인

  ```text
  [brain@class24 ~]$ grep . /etc/*-release
  ```

* 디스크 사용 용량 체크

  ```text
  [brain@class24 ~]$ df -h
  ```

* 용량 확보를 위해서 필요없는 데이터 삭제

  ```text
  [brain@class24 ~]$ rm -r sontestdata/[brain@class24 ~]$ rm Untitled.ipynb[brain@class24 ~]$ rm Anaconda3-2018.12-Linux-x86_64.sh
  ```

* CPU 확인

  ```text
    [brain@class24 ~]$ cat /proc/cpuinfo
  ```

* 메모리 용량 : 16G

  ```text
  [brain@class24 ~]$ cat /proc/meminfo
  ```

## Anaconda 사용

※ Anaconda 설치 완료 상태

* conda, python 버전 확인

  ```text
  conda --versionpython --version
  ```

* conda 가상환경 리스트 확인

  ```text
  conda info --envs
  ```

* 가상환경 새로 생성

  ```text
  conda create --name tacotron python=3.6[brain@class24 ~]$ conda activate tacotron
  ```

## git 설치

* git 설치를 위해 root 계정으로 변경

  ```text
  $ su - 
  ```

* git 설치

  ```text
  [root@class24 ~]# yum install git
  ```

* git clone

  ```text
  $ su - brain[brain@class24 ~]$ git clone https://github.com/keithito/tacotron.git
  ```

* clone된 directory 확인

  ```text
  $ cd tacotron [brain@class24 tacotron]$ ls -al
  ```

## Server에서 실행

※ **conda activate tacotron** : 가상환경이 activate 상태인지 확인할 것!

* tensorflow 설치

  ```text
  (tacotron) [brain@class24 tacotron]$ pip install tensorflow
  ```

* Install requirements

  ```text
  (tacotron) [brain@class24 tacotron]$ pip install -r requirements.txt
  ```

## demo tacotron with pre-trained model

* Download and unpack a model

  ```text
  (tacotron) [brain@class24 tacotron]$ curl http://data.keithito.com/data/speech/tacotron-20180906.tar.gz | tar xzC /tmp
  ```

* Run the demo server

  ```text
  (tacotron) [brain@class24 tacotron]$ python3 demo_server.py --checkpoint /tmp/tacotron-20180906/model.ckpt
  ```

* 방화벽 상태 확인 및 방화벽 해제

  ```text
  [brain@class24 ~]$ systemctl status firewalld [brain@class24 ~]$ systemctl stop firewalld
  ```

* 방화벽 영구 제거

  ```text
    systemctl disable firewalld
  ```

## Run the demo server:

* Browser 접속 :  [http://192.168.113.104:9000/](http://192.168.113.104:9000/)

## LJ dataset download

* Download a speech dataset

  ```text
  (tacotron) [brain@class24 tacotron]$ wget https://data.keithito.com/data/speech/LJSpeech-1.1.tar.bz2
  ```

* unpack tar

  ```text
  (tacotron) [brain@class24 tacotron]$ tar -jxvf LJSpeech-1.1.tar.bz2
  ```

* tree 명령 in Linux

  ```text
  (tacotron) [brain@class24 tacotron]$ ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'(tacotron) [brain@class24 tacotron]$ du -sh * #용량확인 
  ```

## Preprocess the data

```text
  (tacotron) [brain@class24 tacotron]$ python3 preprocess.py --dataset ljspeech
```

## Train a model

```text
  (tacotron) [brain@class24 tacotron]$ python3 train.py
```

## Monitor with Tensorboard

```text
  tensorboard --logdir ~/tacotron/logs-tacotron
```

* Browser 접속 : [http://192.168.113.104:6006/](http://192.168.113.104:6006/) 

## Test

```text
  python3 demo_server.py --checkpoint ~/tacotron/logs-tacotron/model.ckpt-(185000)
```

