# sec_transc

11/9 ejbca root e sub

# EJBCA

* instala o docker e deixa aberto
*  pull keyfactor/ejbca-ce
*  docker run -it --rm -p 80:8080 -p 443:8443 -h localhost -e TLS_SETUP_ENABLED="simple" keyfactor/ejbca-ce
* https://localhost:443/ejbca/adminweb/ -> tem que botar o https
  ![image](https://github.com/user-attachments/assets/2ac16c62-36a2-4702-93c1-4534e43d6eed)
  cancela

  ## Crypto token

* Criar um token novo
  ![image](https://github.com/user-attachments/assets/9d67214b-c335-46bc-8bb5-39bb120d54fe)
* o Código é tipo uma senha
* Escolhe o algoritmo:
 ![image](https://github.com/user-attachments/assets/d33a8108-334f-4cba-9d15-166fecfc6431)
* gera o par de chaves
  ![image](https://github.com/user-attachments/assets/2980136e-0c49-457d-82c1-172e8569aa92)

## Perfil de certificado Root

![image](https://github.com/user-attachments/assets/ab6ce612-9831-41fd-bd58-a3c4a3365e07)
* clonar o profile pra conseguir editar
![image](https://github.com/user-attachments/assets/941dbde8-c31b-42e5-b99a-86dd752133fe)
(20y é a validade)

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
(a root é sefl signed, escolher o perfil cirado)

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





