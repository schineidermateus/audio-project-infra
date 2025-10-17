# 🎧 AudioTools - Processamento de Áudio com NodeJS e Angular

Este é um projeto **full-stack** que permite a manipulação de arquivos de áudio **MP3** (Junção, Corte e Mixagem).  
O **backend** utiliza **NodeJS** para processamento (via **FFmpeg**) e o **frontend** é construído com **Angular** e **Tailwind CSS**, oferecendo uma interface moderna e rápida.

Todo o ambiente de desenvolvimento é **orquestrado e isolado via Docker e Docker Compose**.

---

## 🏗️ Estrutura do Projeto

O projeto é dividido em dois serviços principais:

| Diretório   | Descrição |
|-------------|-----------|
| **backend/**  | Aplicação **NodeJS**, responsável por receber arquivos, processar áudio (usando **FFmpeg**) e devolver o resultado binário. |
| **frontend/** | Aplicação **Angular (Standalone)** com **Tailwind CSS**, responsável pela interface de usuário e comunicação com a API REST. |

---

## 🚀 Requisitos de Execução

Você precisa ter as seguintes ferramentas instaladas em sua máquina:

- Docker
- Docker Compose

---

## ⚙️ Como Executar o Projeto

A execução envolve a construção das imagens e a inicialização dos containers.

### 1. Clonar o Repositório

```bash
# Assumindo que você está na pasta onde deseja clonar o projeto
mkdir projeto-audio
cd projeto-audio
git clone schineidermateus/audio-project-frontend
git clone schineidermateus/audio-project-backend
git clone schineidermateus/audio-project-infra
cd audio-project-infra
```

### 2. Construir e Iniciar os Containers

O arquivo `docker-compose.yml` irá:

- Construir a imagem do **backend** (instalando o FFmpeg e as dependências do NodetJS);
- Construir a imagem do **frontend** (instalando as dependências do Angular).

Comando para construir e subir os serviços:

```bash
docker-compose up --build
```

> **Nota:** Use a flag `--build` sempre que adicionar ou alterar dependências (`package.json`) ou modificar os `Dockerfiles`, para garantir que as imagens sejam reconstruídas corretamente.

### 3. Acessar a Aplicação

Após a inicialização (pode levar alguns minutos na primeira execução), os serviços estarão disponíveis:

| Serviço | Endereço Local | Porta | Descrição |
|---------|----------------|-------|-----------|
| Frontend (Angular) | http://localhost:4200 | 4200 | Interface de usuário |
| Backend (NodeJS API) | http://localhost:3000  | 3000 | API de processamento de áudio |

---

## 🛠️ Comandos de Manutenção do Docker

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `docker-compose down` | Para os containers em execução e os remove. | `docker-compose down` |
| `docker-compose up --build <service_name>` | Reconstrói um serviço específico após alteração de código ou dependências. | `docker-compose up --build backend` |
| `docker-compose logs <service_name>` | Exibe os logs de um container (útil para debug). | `docker-compose logs frontend` |

---

## ⚠️ Observações de Desenvolvimento

- **Hot Reload:** Ambos os containers estão configurados com volumes de desenvolvimento; alterações em arquivos `.ts`, `.html` e `.scss` devem ser refletidas automaticamente no container em execução.
- **CORS:** O backend está configurado para aceitar requisições do frontend (`http://localhost:4200`) em ambiente de desenvolvimento.
- **FFmpeg:** O binário do FFmpeg é instalado diretamente no Dockerfile do backend para garantir que o processamento de áudio funcione dentro do container.

---

📄 **Licença:** Livre para uso educacional e de pesquisa.