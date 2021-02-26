---
title: python configparser
tags: python, configparser
---

프로그램의 중요한 옵션들을 저장하고 관리하기 위해 cfg나 ini 파일 등을 사용한다. 파이썬에서 configparse 패키지를 활용할 수 있다. configparse는 이런 파일들을 읽고, 쓸 수 있는 클래스를 제공한다.

설정 파일은 아래 예시와 같이 작성된다.

~~~
[DEFAULT]
a = a
b = b
c = c

[SECTION]
option1 = a
option2 = b
option3 = c
option4 = d
~~~



설정 파일을 읽기 위해 ConfigParser의 인스턴스를 생성한다. ConfigParser는 read 메소드를 제공하며, 파일 경로를 입력하여 설정 파일을 읽어낸다.

~~~python
from configparse import ConfigParser

parser = ConfigParser()
parser.read('{cfg_file_path}')
~~~

아래 코드를 활용하면 모든 설정 값을 key, value 형태로 읽어들일 수 있다.

~~~python
for section in parser:
    for key in section:
        value = parser[section].get(key)
~~~



또한 설정파일에 주석이 있는 경우에는 ConfigParser 클래스에 comment_prefix 파래미터를 입력하여 제거할 수 있다.

~~~python
from configparse import ConfigParser

parser = ConfigParser(comment_prefix=['#', ';'])
parser.read('{cfg_file_path}')
~~~

