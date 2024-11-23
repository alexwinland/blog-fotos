# Blog de Fotos - API com Node.js & MongoDB 📸✨

Bem-vindo ao projeto **Blog de Fotos API**! 📸 Neste repositório, você aprenderá como criar uma API completa, que inclui upload de imagens, integração com o Google Gemini para geração de descrições automáticas e como usar o MongoDB para armazenar dados de forma eficiente.

<img src="/imagem/Projeto.png">

---

## 🔍 Passo a passo do que foi feito no projeto

- **Node.js** 🖥️: A instalação do Node.js e como iniciar o projeto com **NPM**.
- **Servidor Express** 🌐: Como criar e rodar um servidor com **Express**.
- **MongoDB** 💾: Como configurar o banco de dados no **MongoDB Atlas** e integrá-lo ao projeto.
- **Google Gemini API** 🔑: Como gerar uma **API Key** no Google AI Studio e usar a API para gerar descrições automáticas de imagens.
- **Rotas HTTP** 🔄: Como criar rotas **GET**, **POST**, **PUT** e **DELETE**.
- **Upload de Imagens** 🖼️: Implementação de upload de imagens para o servidor.
- **Deploy na Nuvem** ☁️: Como fazer o deploy do backend na **Google Cloud**.

---

## 🛠️ Ferramentas usadas

- **Node.js** 🖥️
- **Express** 🌐
- **MongoDB** 💾
- **Google Gemini API** 🔑
- **Multer** para upload de imagens 🖼️

---

## 🚀 Como rodar o projeto

### 1. Instalação do Node.js

Se você ainda não tem o **Node.js** instalado, [baixe e instale aqui](https://nodejs.org/). O Node.js é necessário para rodar o backend.

### 2. Inicializando o Projeto

Crie o seu projeto e instale as dependências com o seguinte comando:

```bash
npm init -y
npm install express mongodb dotenv multer @google/generative-ai
```

### 3. Defina suas variáveis de ambiente

Crie um arquivo **.env** para armazenar as variáveis de ambiente, como a **API Key** do Google Gemini:

```env
GEMINI_API_KEY=SuaChaveDaAPI
STRING_CONEXAO=mongodb+srv://usuario:senha@cluster.mongodb.net/instabytes?retryWrites=true&w=majority
```

### 4. Inicie o servidor

Com tudo pronto, inicie o servidor:

```bash
node index.js
```

---

## 🚀 Fazendo o Deploy

Para colocar seu backend na nuvem, faça o deploy usando **Google Cloud Platform**. 🚀✨

1. Acesse o [Google Cloud](https://cloud.google.com/) e crie um projeto.
2. Use o **App Engine** para subir sua aplicação Node.js.
3. Configure seu projeto com o **MongoDB Atlas** e as variáveis de ambiente.

---

## ⚙️ Testando a API

Para testar as rotas da sua API, use o **Postman** ou **ThunderClient**. 

Aqui estão algumas rotas para testar:

- **GET `/posts`**: Para listar todos os posts.
- **POST `/posts`**: Para criar um novo post.
- **POST `/upload`**: Para fazer upload de imagens.
- **PUT `/posts/:id`**: Para atualizar um post.

---

## 🤝 Contribua

Se você quiser ajudar a melhorar o projeto, fique à vontade para abrir um **Pull Request**. Vamos juntos! 😄
