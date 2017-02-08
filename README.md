# Docker WSO2EMM

[![Go to Docker Hub](https://img.shields.io/badge/Docker%20Hub-%E2%86%92-blue.svg)](https://hub.docker.com/r/scoutman57/docker-wso2emm/)

WSO2 EMM Enterprise Mobile Management Docker image
(http://wso2.com/products/enterprise-mobility-manager)

## Installation from Docker Hub

```sh
$ docker pull scoutman57/docker-wso2emm
```

## Building the image from repository
1. clone the repository.
2. cd into the repository.
3. ```docker build -t scoutman57/docker-wso2emm .```

## Usage

```sh
$ docker run --name wso2emm -p 9443:9443 -p 9763:9763 -d scoutman57/docker-wso2emm
```

Then you can access EMM Admin Console in the following URL

```sh
open https://localhost:9443/emm
```

## Configure your server

[Follow the General Server Configurations manual](https://tr.im/5dwWr)

After completing the server configuration modify the following files:

+ app-manager.xml

+ identity.xml

+ sso-idp-config.xml

+ sso-idp-config.xml

+ sso-sp-config.properties

1. **app-mamager.xml** file located in /repository/conf
  Change the below url according to the docker container IP address ``` https://localhost:9443/samlsso {code} For an example, my docker container IP is 172.17.0.2 . So I have changed the url as below {code} https://172.17.0.2:9443/samlsso ```

2. **identity.xml** file located in /repository/conf/identity
  Change the below url according to the docker container IP address ``` https://localhost:9443/samlsso ```

3. **sso-idp-config.xml** file located in /repository/conf/identity
  ``` https://localhost:9443/publisher/acs https://localhost:9443/publisher/acs ``` You can see "localhost" keyword in several urls inside sso-idp-config.xml file .So; if you cannot access any pages in other applications, you can replace the localhost with container IP address.

4. **sso-sp-config.properties** file located in /repository/conf/security directory.
  Change the below url according to the docker container IP address ```SAML2.IdPURL=https://localhost:9443/samlsso ```


## Documentation

* [WSO2 EMM Documentation](https://docs.wso2.com/display/EMM201/WSO2+Enterprise+Mobility+Manager)
