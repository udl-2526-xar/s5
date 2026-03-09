# Sessió 5 (09/03)
## Treballar amb Encrypted Sockets

### Part 1

Modificarem el codi del xat client-servidor de la **Sessió 3** perquè utilitzi **sockets SSL**.

**Instruccions:**

1. Modifica el **Servidor** i el **Client** perquè utilitzin `SSLSockets` en comptes de `Sockets`.
2. Recorda crear:
  - `SSLSocketFactory`
  - `SSLServerSocketFactory`
3. Per fer-ho sense una Autoritat Certificadora (CA) crearem:
  - **Servidor:** un fitxer `server.jks` que contingui un certificat autosignat amb:
    - Clau pública
    - Clau privada  
      *(utilitza la comanda `keytool`)*
  - Exporta el certificat de `server.jks` a un fitxer `server.cer` que li facilitarem al client.
  - Importa aquest certificat a un fitxer `clientTrust.jks` que és el que utilitzarà el client.
4. Revisa i prova amb quines comandes has d’executar els fitxers perquè utilitzin els fitxers creats.

---

### Homework

Què passaria si al **Server** utilitzessis SSL i al **Client** no?  
Prova-ho.