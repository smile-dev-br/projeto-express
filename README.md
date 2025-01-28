# 📜 **Studio Caudas Express 🚀**

Studio Caudas Express é um ambiente de desenvolvimento rápido utilizando **Docker** e **Laravel**. No momento, o projeto está configurado com **Laravel em branco**, mas será expandido para um sistema de desenvolvimento acelerado.

## 📌 Tecnologias Utilizadas
- **Docker + Docker Compose**
- **PHP 8.4 + Laravel**
- **MySQL**
- **Redis**
- **Node.js (para build do frontend com npm)**

---

## 📦 **Instalação e Configuração**
Para rodar o projeto, certifique-se de ter **Docker** e **Docker Compose** instalados.

### 1️⃣ **Clone o repositório**
```bash
git clone https://github.com/seu-repositorio/studio-caudas-express.git
cd studio-caudas-express
```

### 2️⃣ **Crie o arquivo `.env`**
Copie o `.env.example` para `.env`:
```bash
cp .env.example .env
```
Edite o `.env` e ajuste as configurações do banco de dados, se necessário.

---

## 🐳 **Rodando com Docker**
### 3️⃣ **Suba os containers**
```bash
docker-compose up -d --build
```

Isso criará os serviços:
- `backend.studio.caudas.express` → Laravel
- `mysql.studio.caudas.express` → Banco de Dados MySQL
- `redis.studio.caudas.express` → Cache Redis

---

## ⚙️ **Execução de Comandos no Laravel**
Após subir os containers, entre no **container do backend** e execute os seguintes comandos:

### 🔹 **Instalar dependências do Laravel**
```bash
docker exec -it backend.studio.caudas.express bash -c "composer install"
```

### 🔹 **Instalar dependências do Node.js**
```bash
docker exec -it backend.studio.caudas.express bash -c "npm install && npm run build"
```

### 🔹 **Gerar chave do Laravel**
```bash
docker exec -it backend.studio.caudas.express bash -c "php artisan key:generate"
```

### 🔹 **Rodar migrações no banco**
```bash
docker exec -it backend.studio.caudas.express bash -c "php artisan migrate"
```

---

## 🌐 **Acessando a Aplicação**
Após rodar os comandos acima, acesse o Laravel pelo navegador:
```bash
http://localhost
```

Caso tenha mudado as portas, ajuste conforme necessário.

---

## 🔄 **Parar e Remover Containers**
Se precisar parar os containers:
```bash
docker-compose down
```

Para reiniciar os containers sem rebuildar:
```bash
docker-compose up -d
```