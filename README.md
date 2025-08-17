# Criando-Maquina-Virtual-Lab
Este repositório contém a documentação sobre a criação de máquinas virtuais e o processo de configuração de uma instância de Banco de Dados

Projeto: Configurando uma instância de Banco de Dados na Azure

#### Objetivo: Praticar o processo de configuração de uma instância de Banco de Dados na plataforma Microsoft Azure.

## Passo a passo do laboratório

#### 1. Criar Instância Gerenciada de SQL do Azure.

Acesse o Portal Azure.

Pesquise por "SQL managed instances" e clique em "Criar".

Preencha os campos:

Assinatura: Selecione sua conta.

Grupo de Recursos: Crie ou selecione um existente.

Nome da Instância Gerenciada: Ex.: sql-mi-lab.

Região: Escolha uma disponível (ex.: East US).

Computação + Armazenamento:

Tipo de serviço: "Uso Geral" (padrão).

Geração de hardware: Gen5.

vCores: 8 (mínimo recomendado).

Armazenamento: 32 GB (mínimo).

Autenticação:

Login de administrador: Defina um usuário (ex.: mi-admin).

Senha: Crie uma senha forte.

Configurar Rede:

Selecione uma rede virtual existente ou crie uma nova.

A Instância Gerenciada exige uma subnet dedicada (sem outros recursos).

Clique em "Revisar + Criar" e depois em "Criar".

#### 2. Configurar Acesso
A implantação pode levar até 6 horas.

Após a criação, vá até o recurso e:

Libere o tráfego: Em "Segurança" > "Redes", adicione seu IP público ao firewall.

Conecte-se: Use o SQL Server Management Studio (SSMS) ou Azure Data Studio com:

Servidor: sql-mi-lab.xxxxxx.database.windows.net.

Autenticação: SQL Server.

Login/senha: Definidos na criação.

3. Testar a Instância
Execute um comando SQL básico para verificar:

CREATE DATABASE LabDB;
USE LabDB;
CREATE TABLE Teste (ID INT PRIMARY KEY, Nome VARCHAR(50));
INSERT INTO Teste VALUES (1, 'Azure SQL MI');
SELECT * FROM Teste;
