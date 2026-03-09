# Comandes útils per crear fitxers SSL i executar el client/servidor

## 1. Crear el keystore del servidor amb certificat autosignat

```bash
keytool -genkeypair \
  -alias servidorKey \
  -keyalg RSA \
  -keystore server.jks \
  -storepass contrasenyaServer123 \
  -validity 360 \
  -keysize 2048
```

## 2. Exportar el certificat del servidor a un fitxer .cer
```bash
keytool -exportcert \
  -alias servidorKey \
  -keystore server.jks \
  -file server.cer \
  -storepass contrasenyaServer123
```

## 3. Importar el certificat del servidor al truststore del client
```bash
keytool -importcert \
  -alias servidorKey \
  -file server.cer \
  -keystore clientTrust.jks \
  -storepass contrasenyaClient123
```

## 4. Executar el servidor SSL
```bash 
java -Djavax.net.ssl.keyStore=server.jks \
     -Djavax.net.ssl.keyStorePassword=contrasenyaServer123 \
     ConcurrentServerSSL
```

## 5. Executar el client SSL
```bash
java -Djavax.net.ssl.trustStore=clientTrust.jks \
     -Djavax.net.ssl.trustStorePassword=contrasenyaClient123 \
     ClientSSL
```
