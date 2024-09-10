---
{"dg-publish":true,"permalink":"/blog/posts/c-panel-2-c-soluci-c3-b3n-21-mail-delivery-spf-or-dkim-28-29/"}
---


![](../fetched_images\20230808-182745_chrome.png)
En el cPanel ir a la sección de correos; Email Deliverability y entrar a
  Ajustes del dominio que tiene problemas.

  En la seción **DKIM**, precionar el boton **Generate Local DKIM Key**

          Advertencia:
        

            A DKIM key for “mail.aldo.net.ar” does not exist on the local
            server.
          
Generate Local DKIM Key

  Una vez que se generan las claves aplicar las claves.

          Install The Suggested Record
        
Con esto ya debería estar solucionado.
Esta es un ejemplo del error
host gmail\-smtp\-in.l.google.com \[x.x.x.x\]
    SMTP error from remote mail server after end of data:
    550\-5.7.26 This mail is unauthenticated, which poses a security risk to the
    550\-5.7.26 sender and Gmail users, and has been blocked. The sender must
    550\-5.7.26 authenticate with at least one of SPF or DKIM. For this message,
    550\-5.7.26 DKIM checks did not pass and SPF check for \[deocar.com.ar\] did not
    550\-5.7.26 pass with ip: \[x.x.x.x\]. The sender should visit
    550\-5.7.26  https://support.google.com/mail/answer/81126\#authentication for
    550 5.7.26 instructions on setting up authentication. qz11\-20004021qkn.362 \- gsmtp