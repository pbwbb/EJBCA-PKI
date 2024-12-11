em construção...

# EJBCA PKI

Constuindo uma infraestrutura de chaves públicas utilizando o ejbca para criação de autoridades certificados e emissão de certificados digitais.

## instalando o EJBCA

* instalando o docker 
*  pull keyfactor/ejbca-ce
*  docker run -it --rm -p 80:8080 -p 443:8443 -h localhost -e TLS_SETUP_ENABLED="simple" keyfactor/ejbca-ce
* https://localhost:443/ejbca/adminweb/ -> tem que botar o https
  ![image](https://github.com/user-attachments/assets/2ac16c62-36a2-4702-93c1-4534e43d6eed)
  cancela

# CA Root
  ## Crypto token

* Criar um token novo
  ![image](https://github.com/user-attachments/assets/9d67214b-c335-46bc-8bb5-39bb120d54fe)
* o Código funciona como uma senha
* Escolhendo o algoritmo:
 ![image](https://github.com/user-attachments/assets/d33a8108-334f-4cba-9d15-166fecfc6431)
* gerando o par de chaves
  ![image](https://github.com/user-attachments/assets/2980136e-0c49-457d-82c1-172e8569aa92)

## Perfil de certificado Root

![image](https://github.com/user-attachments/assets/ab6ce612-9831-41fd-bd58-a3c4a3365e07)
* clonar o profile pra conseguir editar
![image](https://github.com/user-attachments/assets/941dbde8-c31b-42e5-b99a-86dd752133fe)
(vou usar 20 anos como validade)

![image](https://github.com/user-attachments/assets/a41080d0-589a-498a-8e86-5bf2e8010fe6)

* CRL distribution point -> url da CRL
* Authority Information Access	-> url da CA e OSCP

![image](https://github.com/user-attachments/assets/6b8ba6b2-13aa-47e7-81ac-3e0afd93dbc8)

![image](https://github.com/user-attachments/assets/23a815fd-31a2-4e49-baa7-f45fe4a47c40)


## Criar CA Root

![image](https://github.com/user-attachments/assets/0bdec1d8-db9d-47cf-aedf-da4d82b69340)

* escolher o crypto token
* usar mesmo algoritmos do token
![image](https://github.com/user-attachments/assets/c66cf240-209b-4e2f-ba68-83d8da55609f)

![image](https://github.com/user-attachments/assets/24474c34-76c9-4825-a9f0-8c6858894b60)
(a root é self signed, escolher o perfil criado)

* o resto dos campos não foi mexido

## Baixar certificado da Root

https://localhost/ejbca/ra/cas.xhtml

![image](https://github.com/user-attachments/assets/a6c05df8-8bfe-4523-a9aa-c49ae16889df)
* Mudei a extensão para conseguir visualizar no windows
![image](https://github.com/user-attachments/assets/da7e9244-7718-4e96-8a9f-3cae1bdcbec2)
![image](https://github.com/user-attachments/assets/f25fec99-fb99-47f1-b3c9-30f7964cf332)


## instalar certificado

* configurações do edge -> Gerenciar Certificados -> import
![image](https://github.com/user-attachments/assets/0f064a70-2164-44ad-9f9a-c66fc6ffee7e)
* Ou abrir o certificado e clicar em instalar

# CA Subordinada

## Perfil de certificado da CA subordinada

* Clonar o perfil
![image](https://github.com/user-attachments/assets/4b7421d6-3679-4f03-afd8-fbf90a9a7d8a)

![image](https://github.com/user-attachments/assets/799e38ca-cb4e-493b-9f7f-a33483f0de4a)

![image](https://github.com/user-attachments/assets/7950ade9-8678-42a9-983d-59ad7ddf930f)

* criar um novo crypto token para a CA subordinada
![image](https://github.com/user-attachments/assets/efa58573-1a0f-4382-ad6f-968f600ac191)

## Criar CA Subordinada

* escolher crypto token
![image](https://github.com/user-attachments/assets/4960c4ed-1907-4744-8a4a-0147ae724d84)
* Escolher o perfil da Sub CA
* A Sub CA é assinada pela Root
![image](https://github.com/user-attachments/assets/da03f722-ef3f-4125-824c-1fc069a0e2ff)
![image](https://github.com/user-attachments/assets/20118b71-a430-4333-be3a-8ef789579209)

## Baixando certificados

![image](https://github.com/user-attachments/assets/81d89a86-d4fa-46ef-b694-1ff22fab7b63)
(A CA subordinada aparece indentada)
![image](https://github.com/user-attachments/assets/cf18c406-c7d6-4135-9a56-a78a4728a2d6)
![image](https://github.com/user-attachments/assets/5bc36ab8-01a2-451f-a6bc-9dfe2e2a7bd9)

## Perfil para Assinatura de e-mail

* x

  
# Assinatura de Código

* Para a assinatura de código sera usado o windows SDK

## Perfil code-signing

* clonar o enduser

![image](https://github.com/user-attachments/assets/156c0b02-d913-4ea3-a139-ef0a0673de79)

![image](https://github.com/user-attachments/assets/baf3e692-dd24-41d7-8e6f-03f193afcdf6)

* Code Signing

![image](https://github.com/user-attachments/assets/819abaef-cca7-43f4-ad14-390d16c185fa)

![image](https://github.com/user-attachments/assets/08773be2-522e-4a8f-9cd0-84d5cfc0111d)

## Perfil de entidade final

![image](https://github.com/user-attachments/assets/74d2e18b-8867-4af0-8f43-61cdbeb88f43)

![image](https://github.com/user-attachments/assets/7d6712b6-582e-4944-afc0-ee2eb3e4a40b)

![image](https://github.com/user-attachments/assets/008e1569-0724-4092-86d2-d58b511714c2)

![image](https://github.com/user-attachments/assets/44461df6-22b0-46cb-b5bf-e5af6d5e45eb)

## Solicitando o certificado

![image](https://github.com/user-attachments/assets/f16cb990-dc9c-4141-a3a7-0ac0b163b961)

![image](https://github.com/user-attachments/assets/24a55b28-92b0-46c1-a21b-5edc4ea4ea6f)

![image](https://github.com/user-attachments/assets/6f80718f-2569-4c4d-ac63-a5323b48cbbb)

(o código é uma senha qualquer)

* baixando o PKCS12

![image](https://github.com/user-attachments/assets/6fb1ae59-8b23-4ee2-9ff5-6a85e4a2f25f)

* importando o Certificado

![image](https://github.com/user-attachments/assets/33c002e1-892b-444e-b757-3bec440ea6a0)

* senha que botou antes

![image](https://github.com/user-attachments/assets/d46cd659-1bb2-4dfd-bf88-ee3b3e4c2a92)

(se não bota aqui)
![image](https://github.com/user-attachments/assets/97e33562-f060-4a0a-8c84-42b2870cc5fb)

![image](https://github.com/user-attachments/assets/36cbaff6-40fa-400d-aba0-f0a6e6b9930d)

## Usando o Sgintool

* Fazer instalação do windows SDK -> https://developer.microsoft.com/en-us/windows/downloads/windows-sdk/
* Adicionar Variavel no PATH
** Editar variaveis do sistema

![image](https://github.com/user-attachments/assets/42651439-3c5a-4f99-bd19-d15cea5c99fb)

![image](https://github.com/user-attachments/assets/189f09f2-01c8-4e56-862a-8f7f4f93dffe)

(C:\Program Files (x86)\Windows Kits\10\bin\10.0.26100.0\x86)

* cd C:\Program Files (x86)\Windows Kits\10\bin\10.0.26100.0\x86
* signtool sign /? -> menu help
* Nesse caso vou assinar uma cópia do notepad
* signtool sign /a <caminho>

![image](https://github.com/user-attachments/assets/77ba4283-ad03-4bb0-9827-ea6260b507a7)

* Nesse caso é preciso inserir um algoritmo de hash (digest), vou usar SHA256
* signtool sign /a /fd SHA256 <caminho>

![image](https://github.com/user-attachments/assets/5d22f8b3-c37c-4f89-9a62-aa1d63497686)

![image](https://github.com/user-attachments/assets/f34b937a-2476-4048-95b6-ba68774c72e2)

![image](https://github.com/user-attachments/assets/f80d7514-94a9-44ea-a17a-fbafd4c6ae9f)

## Incluindo timestamp com a freetsa

* Vou assinar o notepad novamente incluindo a timestamp
URL -> http://freetsa.org/tsr
* signtool sign /a /fd SHA256 /tr http://freetsa.org/tsr /td SHA256 C:\Tmp\notepad.exe
![image](https://github.com/user-attachments/assets/35ac1a0e-69e1-4aa8-bc99-a2858fa6ff3d)

* depois de instalar o certificado da freetsa conseguimos verificar a timestamp

![image](https://github.com/user-attachments/assets/855e25f8-f069-460b-a221-c2b34c8460ef)

# Certificado para servidor web TLS

## perfil do server

* clonar o perfil server

   ![image](https://github.com/user-attachments/assets/12e9c4ec-c00a-47b2-b9ab-a84a892b2385)

![image](https://github.com/user-attachments/assets/b45a0d38-3a87-40b2-a203-fafa6c9aac8d)

![image](https://github.com/user-attachments/assets/f8bfd9d2-e75c-4b85-9705-a478c340c8a5)

![image](https://github.com/user-attachments/assets/3bc2a15f-31f0-4904-9cd8-19dd8dbe7c92)

## Perfil de entidade final

![image](https://github.com/user-attachments/assets/f68e1f5d-35ac-4249-8353-e1f55c24ddf3)

![image](https://github.com/user-attachments/assets/a84556ed-9e02-4d4d-9018-76ff9ed89172)

* O par de chaves é gerado pela propria entidade final

![image](https://github.com/user-attachments/assets/08c3bb46-1ddd-4656-8f9d-d8c64c36d1be)


![image](https://github.com/user-attachments/assets/a6845aee-6e92-4cb1-b5cc-84cc6da83f02)

# Windows IIS

* internet information services manager
* Server certificates
  
 ![image](https://github.com/user-attachments/assets/0a8e753f-3f9b-4ead-b347-3a063d81635e)

* create certificate request

![image](https://github.com/user-attachments/assets/daaf4e07-f339-4490-9d33-9843c6844cc9)

![image](https://github.com/user-attachments/assets/45ba04e7-3cdb-4517-b011-71a8cca833a3)

![image](https://github.com/user-attachments/assets/bc5aeb4f-f987-4b55-8431-3c035ccfd3ca)

![image](https://github.com/user-attachments/assets/072ee23b-b3ea-42a8-ae15-5ea54bd0805c)


https://www.filepastebin.com/ (passsa o cert pra maquina do ejbca)

* Solictar certificado

![image](https://github.com/user-attachments/assets/8231cf6e-2c06-4ed3-9909-824de2c379c0)

* colar o request

![image](https://github.com/user-attachments/assets/12841e17-86d2-475d-bb2e-37352c404a7b)

* baixar como pkcs7 depois manda ele pro server

* complete certificate request

![image](https://github.com/user-attachments/assets/0924a35f-0d27-44c6-895e-bade4d29ea27)

![image](https://github.com/user-attachments/assets/28615493-3b4f-4242-8338-46e2ff99d809)

![image](https://github.com/user-attachments/assets/59e8174f-4680-4ee2-bd27-b95e06b345fd)

![image](https://github.com/user-attachments/assets/34cc0492-3bf4-473b-85f3-016ba6b2b4f9)


* instala o cert

![image](https://github.com/user-attachments/assets/0d9ff259-0b24-444a-bd93-867d9f8913b6)

* mudar o hosts para acessar o site (C:\Windows\System32\Drivers\etc\hosts)
 IP dominio_do_server

## revogar certificado tls

* search end entity

![image](https://github.com/user-attachments/assets/ef7e5882-8780-44d4-b0ef-26ff347b6f75)
* revoke selected
* criar crl

![image](https://github.com/user-attachments/assets/a1984ac8-4a8d-4c44-933b-67a6d9ef122a)


## wireshark  
* tls.handshake
* client hello

![image](https://github.com/user-attachments/assets/d201e36d-66f7-4007-8d2a-634bb9757486)

![image](https://github.com/user-attachments/assets/27fe8b5b-1596-415a-b370-1cdb4ae440fd)
(ip.addr ip do server, olha pelo session id )

certutil -url url_da_crl



11/9 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2811%5F9%29%2D20240911%5F193819%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E60a53abe%2D8458%2D4c14%2Daedf%2Db3c7a37a7ecf

25/09 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2825%5F9%29%2D20240925%5F193911%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Eab402aba%2D51b8%2D4145%2D9494%2D134aec84bab7

16/10 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2816%5F10%29%2D20241016%5F193944%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Ec4f3274e%2D7e7a%2D4cb5%2Db798%2Dba1b46836c28

16/10 p2 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2816%5F10%29%2D20241016%5F210250%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E0527e1d1%2D9685%2D4da1%2Db45b%2D7df0b3e0368b

23/10 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2823%5F10%29%2D20241023%5F193751%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E6d6538e8%2D8f9f%2D4fcf%2Dac66%2Dc3a698d3b2f8

30/10 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20presencial%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20em%20SL%20%2830%5F10%29%2D20241030%5F193919%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E109db90d%2Df8a9%2D40cd%2Db895%2D79745a41d4e1


06/11 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%286%5F11%29%2D20241106%5F210800%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Ede5fa15e%2Dcb8c%2D4952%2D8277%2Df28e201b0eaf

13/11 -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20presencial%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%2D%20campus%20POA%20%2813%5F11%29%2D20241113%5F193529%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Efea7e0ea%2D4c02%2D4703%2D9094%2Db9ba8a4a860b

correcao GB -> https://asavbrm.sharepoint.com/sites/2024_2943320_1_8/_layouts/15/stream.aspx?id=%2Fsites%2F2024%5F2943320%5F1%5F8%2FDocumentos%20Compartilhados%2FGeneral%2FRecordings%2FExibir%20Apenas%2FAula%20remota%20de%20Seguran%C3%A7a%20em%20Transa%C3%A7%C3%B5es%20Eletr%C3%B4nicas%20%284%5F12%29%2D20241204%5F193913%2DGrava%C3%A7%C3%A3o%20de%20Reuni%C3%A3o%2Emp4&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E28081eb3%2D09eb%2D4031%2Dab14%2D8b865821bc72

OID CPS -> 1.3.6.1.5.5.7.2.1

vm -> 74.179.81.143:3389


CA root

- crypto token
- certificate profile
- criar ca
- exemplo gb
    - DN: CN= {Sobrenome} – GB - Root CA,
    O=Unisinos, C=BR.
    - Validade de 20 anos;
    - RSA 4096 bits.

Code sign 

- crypto token
- sub certificate profile
- criar SUBca
- end entity CERTIFICATE profile
- end entity profile
- solicitar certificado no ra web
- instala o querido
- signtool sign /a /fd SHA256 /tr http://freetsa.org/tsr /td SHA256 C:\Tmp\notepad.exe

Email

- Crypto token
- sub Certificate profile
- Criar SubCA
- end entity CERTIFICATE profile
- end entity profile
- solicitar certificado no ra web
    - enviar o pkcs#12 a vm do thunderbird (envia junto o da sub)
    - adicionar os cert no thunderbird
        - PKCS12 → your certificates
        - SubCA → edit trust → mail users
- Quando for enviar o email clica no S/MIME e escolhe se que criptografar ou assinar

Tls

- crypto token
- sub Certificate profile
- criar SUBca
- end entity CERTIFICATE profile (clona o SERVER)
    - ext → server authentication
- end entity profile
    - user generated
        
        ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/55047e25-ea80-424c-911c-ced2625e1d6d/3e9d7e5d-300e-4ab5-a5a2-6ef8f61b8870/image.png)
        
- Criar CSR no web server
- Solicitar certificado no RA web
    - Provided by user e colar a csr
    - baixa o pksc#7 e manda ele pro server
- Complete certification request
    - escolhe o p7b
    - web hosting
    - bindings
- se precisar editar o hosts
    - abre o notepad como admin
    - C:\\Windows\\System32\\Drivers\\etc\\hosts

Revogar cert

- Search end entities
    - acha o cert
- revocation reason
    - se nao tiver bota key compromise fds
    - revoke selected
- CA structure & CRls
    - create CRL na sub ca mesmo
- baixa a CRL da sub CA no RA web

- urls no profile
- DN vai na hora de criar a CA
- extended key use no profile do end entity
- quando for baixar o certificados da CAs baixa o pem sem o chain

  
