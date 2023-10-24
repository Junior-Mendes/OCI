Implantação nó único FortiGate-VM 

Etapa 1 Criando a virtual Cloud Network (VCN) e subnets públicas. 

Passo 1 Na OCI, clique no menu sanduiche e vá para Network> Virtual Cloud Networks, e click em Create Virtual Cloud Network. 

![image](https://github.com/Junior-Mendes/OCI/assets/63074320/e1e5e71f-a9af-4485-954f-6ce9c23ecbd5)

Passo 2 Escolha o nome, o compartment e o bloco de IP para a sua VCN e clique em Create VCN 

![image](https://github.com/Junior-Mendes/OCI/assets/63074320/a3741725-ca13-4aba-ae64-7c936d79c9e0)

Passo 3 Após acessar a sua VCN criada crie um serviço de Internet Gateway
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/630a53d7-767a-416f-abd2-b16373f7f4d6)

Passo 4 Adicione o nome e clique em Create Internet Gateway
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/f537e05e-0e22-4b97-99fe-65296059ffec)

Passo 5 Acessar a tabela de rota default
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/c57414ef-9e79-4ca4-9eb0-add02a49e7c0)

Passo 6 adicione uma nova entrada de rota default direcionando para o serviço de internet Gateway anteriomente criado.
Adicionando o Type Target, Destination CIDR Block e Target Internet Gateway
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/f4444b5d-efdb-45c9-b4d2-133e749d334a)

Passo 7 Na VCN crie uma Subnet em: Networking> Virtual cloud networks>Virtual Cloud Network Details>Subnets

![image](https://github.com/Junior-Mendes/OCI/assets/63074320/40106fa6-04b3-4b7d-b078-7a4b517d7e54)

Clique em create subnet e adicione os sequintes registros

Name; Subnet Access: Public Subnet; Routing Table; Security List
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/383c5a79-8a8c-4e34-a852-aafd97876c44)

Etapa 2 Criar Securtity List

Passo 1 Clique em Default Security List para a rede 10.0.0.0/24

![image](https://github.com/Junior-Mendes/OCI/assets/63074320/996fe8b5-c55e-471b-93a7-98e33eb27d5c)

Por padrão a porta 22 é liberada, vamos adicionar a regra para liberar a porta TCP 443 (https) para ter acesso ao FortiGate via Https e SSH

Clique em Add Ingress Rule e adicione a seguinte entrada.
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/ceb6d958-971f-4e7f-8731-139b3b42d38a)


Para saber todas as portas necessárias para serem liberadas veja em FortiGate open ports.

Etapa 3 Criando uma route table para a rede interna

Passo 1  Precisamos alterar o gateway padrão da rede protegida e apontalo para a segunda interface do FortiGate-VM. Vá para Route Tables>Create Route Table.
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/de28f3de-7104-4fb0-a097-c107d315d617)

Passo 2 Para todos os destinos adicione o internet Gateway por enquanto, vamos altera-lo mais tarde.
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/a5817537-aea8-4b96-80a4-1930f23d0f57)

Etapa 4  Criando uma subnet privada

Passo 1 Crie uma subnet privada, selecione a route table criada anteriormente para a rede privada e marque a opção PRIVATE SUBNET.
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/978a1d9e-8d1e-4c18-a19f-c70e2e129575)

Etapa 4 Criando uma instancia FortiGate-VM importando um arquivo de imagem


Vá em https://support.fortinet.com/download/firmwareimages.aspx  faça seu registro e após logar vá em Support>VM Images


![image](https://github.com/Junior-Mendes/OCI/assets/63074320/cac46a4f-f26d-47fd-92f8-35aed3f4f75a)

Selecione o produto a plataforma OCI e a versão desejada e clique em Download.

![image](https://github.com/Junior-Mendes/OCI/assets/63074320/9c3d2f4b-30cd-47fb-9e49-f472d7c84893)

Importe o arquivo de download .out para o bucket da OCI.










