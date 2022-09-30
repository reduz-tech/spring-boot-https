# Ciando Aplicação Segura
Essa aplicação faz parte do artigo disponível no [](), meu objetivo é abordar um tema bastante necessário no desenvolvimento de software e muitas vezes desconhecido da grande maioria dos devs, uso de certificados em aplicações Java.

Logo abaixo apresento algumas informações resumidas, para acessar o conteúdo completo acesse []().

## Geração do Certificado
A geração do certificado pode ser realizada usando a ferramenta ``keytool`` disponível no JDK e com a ferramenta ``mkcert``, como dito acima, as vantagens e desvantagens estão detalhadas no link []().

### Usando ``keytool``

~~~sh
$ mkdir ./src/main/resources/keystore
$ keytool -genkeypair -alias springboot -keyalg RSA -keysize 4096 -storetype PKCS12 -keystore ./src/main/resources/keystore/springboot.p12 -validity 3650 -storepass password
~~~

### Usando ``mkcert``

~~~sh
$ mkcert -install
$ mkcert dev.reduz.tech test.reduz.tech localhost 127.0.0.1 ::1

# Opcional -certfile CACert.crt
$ openssl pkcs12 -name reduz -export -out certificado.pfx -inkey dev.reduz.tech+4-key.pem -in dev.reduz.tech+4.pem
$ keytool -importkeystore -srckeystore certificado.pfx -srcstoretype pkcs12 -destkeystore springboot.p12
~~~

## Configuração do Certificado

# Referências
* [mkcert](https://github.com/FiloSottile/mkcert)