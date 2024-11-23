Claro! Aqui está um modelo de **README.md** descontraído e com emojis, que descreve o passo a passo do seu projeto. O código também está incluso, conforme solicitado. Fique à vontade para personalizar conforme necessário.

---

# 📸 Blog de Fotos - API com Node.js & MongoDB

Bem-vindo ao repositório do nosso **Blog de Fotos**! 📸✨

Aqui, você vai aprender e implementar desde a criação de uma API, até o deploy na nuvem utilizando o **MongoDB** e a **API Gemini**. Vem com a gente nessa jornada! 😎🚀

---

## 🚀 O que vamos aprender

Nesta aula, vamos:

1. 🖥️ **Instalar o Node.js**
2. 🌐 **Criar e subir um servidor**
3. 🔑 **Gerar a chave da API do Gemini**
4. 📡 **Criar uma base de dados**
5. 💾 **Armazenar dados no MongoDB**
6. 🛠️ **Adicionar rotas**
7. 🖼️ **Fazer upload de imagens**
8. 🔄 **Integração com o frontend**
9. ☁️ **Fazer deploy na Google Cloud**

---

## 📝 Como rodar o projeto

### 1. Instalação do Node.js

Primeiro, instale o [Node.js](https://nodejs.org/) na sua máquina. Vamos precisar dele para rodar o backend.

### 2. Criando o projeto com NPM

No terminal, crie o seu projeto Node.js com:

```bash
npm init -y
```

Isso cria o seu **`package.json`**. Agora, vamos instalar as dependências.

### 3. Instalar Dependências

Vamos instalar as bibliotecas necessárias:

```bash
npm install express mongodb dotenv multer
```

- **express**: Para o servidor web.
- **mongodb**: Para conectar com o MongoDB.
- **dotenv**: Para gerenciar variáveis de ambiente.
- **multer**: Para fazer upload de arquivos.

---

## 🧑‍💻 Código fonte

Aqui está a estrutura do nosso projeto:

### 🚀 **Server**

O servidor Node.js usando **Express** está configurado da seguinte forma:

```javascript
import express from "express";
import routes from "./src/routes/postsRoutes.js";

const app = express();
app.use(express.static("uploads"))
routes(app)

// Inicia o servidor na porta 3000 e exibe uma mensagem no console
app.listen(3000, () => {
    console.log("Servidor escutando...");
});
```

---

### 💾 **Banco de Dados (MongoDB)**

Nosso banco de dados está configurado para se conectar ao **MongoDB Atlas** (ou local, se preferir).

A função `conectarAoBanco` se encarrega de conectar ao banco:

```javascript
import { MongoClient } from 'mongodb';

export default async function conectarAoBanco(stringConexao) {
  let mongoClient;

  try {
      mongoClient = new MongoClient(stringConexao);
      console.log('Conectando ao cluster do banco de dados...');
      await mongoClient.connect();
      console.log('Conectado ao MongoDB Atlas com sucesso!');

      return mongoClient;
  } catch (erro) {
      console.error('Falha na conexão com o banco!', erro);
      process.exit();
  }
}
```

---

### 📝 **Funções de CRUD**

Aqui temos as funções para buscar, criar e atualizar posts no banco de dados:

```javascript
import { MongoClient } from 'mongodb';

export async function getTodosPosts() {
    const db = conexao.db("instabytes");
    const colecao = db.collection("posts");
    return colecao.find().toArray();
}

export async function criarPost(novoPost) {
    const db = conexao.db("instabytes");
    const colecao = db.collection("posts");
    return colecao.insertOne(novoPost);
}

export async function atualizarPost(id, novoPost) {
    const db = conexao.db("instabytes");
    const colecao = db.collection("posts");
    const objID = ObjectId.createFromHexString(id);
    return colecao.updateOne({_id: new ObjectId(objID)}, {$set:novoPost});
}
```

---

### 🖼️ **Upload de Imagens**

Agora, o upload de imagens é feito com o **Multer**, e a imagem é salva no diretório `uploads/`:

```javascript
import fs from "fs";

export async function uploadImagem(req, res) {
    const novoPost = {
        descricao: "",
        imgUrl: req.file.originalname,
        alt: ""
    };

    try {
        const postCriado = await criarPost(novoPost);
        const imagemAtualizada = `uploads/${postCriado.insertedId}.png`
        fs.renameSync(req.file.path, imagemAtualizada)
        res.status(200).json(postCriado);  
    } catch(erro) {
        console.error(erro.message);
        res.status(500).json({"Erro":"Falha na requisição"})
    }
}
```

---

### 🔄 **Rotas da API**

Aqui estão as rotas para o backend:

- **GET `/posts`**: Para listar todos os posts.
- **POST `/posts`**: Para criar um novo post.
- **POST `/upload`**: Para fazer upload de imagens.
- **PUT `/posts/:id`**: Para atualizar um post.

---

## 🔑 Criar sua API Key no Google AI Studio (Gemini)

1. Acesse o **Google AI Studio** e crie um projeto.
2. Gere a **API Key** e guarde ela com carinho! 😄
3. Use essa chave para integrar o **Gemini** ao seu backend e gerar descrições automáticas para as imagens.

---

## 🌍 Deploy

Depois de tudo configurado, é hora de fazer o **deploy** na Google Cloud! 🌐

Siga o tutorial oficial da Google para subir o seu backend com Node.js na **Google Cloud Platform**.

---

## 🔧 Testando a API

Você pode testar a API com ferramentas como **Postman** ou **ThunderClient**. Aqui estão algumas rotas para testar:

- **GET** `/posts` para listar os posts.
- **POST** `/posts` para criar um novo post.
- **POST** `/upload` para fazer upload de imagens.
- **PUT** `/posts/:id` para atualizar um post.

---

## 👋 Contribua

Se você quiser contribuir para o projeto, fique à vontade para fazer um **fork** e enviar **pull requests**. Vamos adorar!
