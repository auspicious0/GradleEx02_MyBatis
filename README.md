# GradleEx02_Mybatis

## 0.	목표

gradle과 mybatis를 활용하여 linux 환경에서 mariadb, oracle의 database(table) 정보를 가져오고 암복호화를 수행하도록 한다.

## 1.	java, configuration source

자바 소스 및 configuration source는 아래 링크를 통해 확인할 수 있다.

[소스 링크](https://github.com/auspicious0/connect_mybatis_db)

oracle의 configuration은 조금 상이한 부분이 있다.

일단 ojdbc library를 추가해야 하고

아래와 같이 작성해야 한다.

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
  PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-config.dtd">

<configuration>
    <typeAliases>
        <typeAlias type="Gradle.User" alias="User"/>
    </typeAliases>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="oracle.jdbc.driver.OracleDriver"/>        
                <property name="url" value="jdbc:oracle:thin:@*.*.*.*:1521:ORCL"/>
                <property name="username" value="id"/>
                <property name="password" value="password"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <mapper resource="mapper/UserMapper.xml"/>
    </mappers>
</configuration>


```


## 2.	build.gradle 소스

build gradle에 필요한 libray 를 추가하고 gradle task – jar로 빌드한다.

자세한 내용은 아래 링크를 참고한다.

[참고 링크](https://github.com/auspicious0/GradleEx01)

## 3.	sh 

shell 파일을 만들고 실행한다. shell 파일에 관한 설명은 민감한 정보이기 때문에 공개하지 않는다.

아래는 실행 결과이다.

아래 maria db가 

![image](https://github.com/auspicious0/GradleEx02_MyBatis/assets/108572025/2f0f9ecd-0bb0-4861-842b-ce8460fe0462)

출력되는 것을 볼 수 있다.

![image](https://github.com/auspicious0/GradleEx02_MyBatis/assets/108572025/d4701683-d1dc-4699-9cb3-565c873c5e4d)

또한 oracle의 table 역시

![image](https://github.com/auspicious0/GradleEx02_MyBatis/assets/108572025/be2bd734-89b9-4889-9170-3af050784bf6)

아래와 같이 출력된다.

![image](https://github.com/auspicious0/GradleEx02_MyBatis/assets/108572025/e97a7be2-a73d-4f57-963d-4424d4291a67)


