# 🎵 Sistema Musical

Um sistema web completo e funcional desenvolvido em **PHP** e **MySQL** para gerenciamento de artistas, álbuns e biblioteca de músicas. O sistema conta com controle de acesso por sessão, upload e redimensionamento automático de imagens, além de integração com links do YouTube.

---

## 🚀 Funcionalidades

### 🔐 Autenticação e Segurança

- Login e logout com controle de sessão PHP (`valida_sessao.php`).
- Criptografia de senhas utilizando hash **BCrypt** (`password_hash` e `password_verify`).
- Proteção contra **SQL Injection** utilizando *Prepared Statements*.
- Prevenção de ataques **XSS** sanitizando saídas com `htmlspecialchars()`.

### 🎤 Gerenciamento de Artistas (CRUD)

- Cadastro, edição, listagem e remoção de artistas.
- Upload de foto do artista com validação e redimensionamento automático via biblioteca **GD**.
- Trava de segurança: impede a exclusão de artistas que possuem músicas cadastradas.

### 🎵 Gerenciamento de Músicas (CRUD)

- Cadastro e edição de músicas associadas a um artista.
- Upload da foto de capa do álbum.
- Extração automática do ID de vídeos do YouTube para exibição de link direto.
- Armazenamento opcional de letras de músicas.

### 🎼 Biblioteca Musical & Filtros

- Visualização de todas as músicas cadastradas.
- Filtro combinável por termo de busca geral (título, artista ou álbum), artista específico e gênero.
- Preservação dos filtros ativos após a realização de ações (como exclusões).

---

## 🛠️ Tecnologias Utilizadas

- **PHP 8.x** (nativo)
- **MySQL / MariaDB** (driver `mysqli`)
- **HTML5 & CSS3** (layout responsivo e estilizado)
- **Biblioteca PHP GD** (processamento de imagens)

---

## 📁 Estrutura de Arquivos

```text
.
├── bd.sql                 # Script SQL para criação do banco de dados
├── conexao.php            # Configuração e conexão com o banco MySQL
├── valida_sessao.php      # Middleware/inclusão para validação de login
├── login.php              # Tela e processamento de login
├── logout.php             # Encerramento de sessão
├── index.php              # Painel/menu principal do sistema
├── cadastro_artista.php   # CRUD de artistas e upload de foto
├── cadastro_musica.php    # CRUD de músicas, capa de álbum e link YouTube
├── listagem_musicas.php   # Biblioteca com filtros de busca
├── geraSenha.php          # Utilitário para gerar hash de senha inicial
├── styles.css             # Estilos do sistema
└── img/                   # Diretório onde as imagens enviadas são salvas
```

---

## ⚙️ Como Executar o Projeto

### Pré-requisitos

Servidor web local como **XAMPP**, **WAMP**, **Laragon** ou ambiente **LAMP/LEMP** com:

- PHP 7.4 ou superior (com extensão **GD** habilitada).
- Servidor MySQL ou MariaDB.

### Passo a Passo

1. **Clonar/Baixar o repositório:**

   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   ```

2. **Configurar o Banco de Dados:**

   - Abra o seu gerenciador de banco de dados (ex.: phpMyAdmin, DBeaver).
   - Importe e execute o arquivo `bd.sql`.
   - Certifique-se de criar a tabela `usuarios` e inserir ao menos um usuário de teste com a senha hash gerada pelo `geraSenha.php`.

3. **Ajustar as credenciais de conexão:**

   Abra o arquivo `conexao.php` e ajuste os dados conforme o seu ambiente local:

   ```php
   $servername = "localhost";
   $username   = "root";
   $password   = "sua_senha";
   $dbname     = "sistema_musical_v2";
   ```

4. **Acessar a aplicação:**

   - Coloque os arquivos na pasta do servidor web (ex.: `htdocs` no XAMPP).
   - Acesse no navegador: `http://localhost/seu-projeto/login.php`

---

## 🔑 Credenciais Padrão (Ambiente de Teste)

| Campo   | Valor   |
|---------|---------|
| Usuário | `admin` |
| Senha   | `123`   |

> ⚠️ **Atenção:** altere essas credenciais antes de colocar o sistema em qualquer ambiente de produção.

---

## 📄 Licença

Este projeto foi desenvolvido com fins educacionais e de aprendizado em desenvolvimento web com PHP e MySQL. Sinta-se livre para utilizar, alterar e aprimorar o código!
