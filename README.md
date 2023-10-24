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

Por padrão a porta 22 é liberada, vamos adicionar a regra para liberar a porta TCP 443 (https)

Clique em Add Ingress Rule e adicione a seguinte entrada.
![image](https://github.com/Junior-Mendes/OCI/assets/63074320/ceb6d958-971f-4e7f-8731-139b3b42d38a)















