# Rec-bancoDeDados-3AT
Desafio de Recuperação: Modelagem e Persistência de Dados (SQLite3)

Nesta tarefa, você não terá os comandos de "copiar e colar". Você deve demonstrar que compreende a sintaxe do SQLite3 e o fluxo de versionamento com Git para resolver um problema de organização de dados.

O Cenário

Você foi contratado para criar o sistema de uma biblioteca. Sua missão é criar um banco de dados que armazene informações sobre  **livros**  e garantir que esses dados sejam enviados corretamente para o GitHub.

----------

 Etapa 1: Criação do Banco de Dados

No terminal do seu Codespace, crie um arquivo de banco de dados chamado  `biblioteca_[seu_nome].db`.

> **Dica:**  Lembre-se do comando utilizado para iniciar o SQLite especificando um arquivo.

 Etapa 2: Estruturação da Tabela (DDL)

Crie uma tabela chamada  `livros`. Você deve definir os tipos de dados corretamente para as seguintes colunas:

1.  **id**: Deve ser a Chave Primária e incrementar automaticamente.
2.  **titulo**: Texto, preenchimento obrigatório (**NOT NULL**).
3.  **autor**: Texto, preenchimento obrigatório.
4.  **ano_publicacao**: Um número inteiro.
5.  **isbn**: Um código de texto que deve ser  **único**  (não pode haver dois livros com o mesmo ISBN).

🛠️ Etapa 3: Manipulação de Dados (DML)

Agora, popule o seu banco de dados:

-   Insira  **pelo menos 5 livros**  de sua preferência.
-   **Desafio Extra:**  Tente inserir um livro com o mesmo  `isbn`  de outro já cadastrado e observe o que acontece (isso testará sua restrição de UNIQUE).

🛠️ Etapa 4: Consulta e Validação

Antes de sair, execute um comando que selecione  **apenas**  o  `titulo`  e o  `autor`  de todos os livros cadastrados, ordenados pelo  `ano_publicacao`.

> **Comando de saída:**  Finalize a sessão do SQLite corretamente.

----------

Entrega Obrigatória (Git)

Não basta criar o arquivo; ele precisa estar no seu repositório remoto. Execute os comandos de Git para:

1.  Adicionar o arquivo  `.db`  específico ao índice.
2.  Criar um commit com uma mensagem profissional (ex: "feat: estrutura e dados da biblioteca finalizados").
3.  Enviar as alterações para o branch  `main`.

----------

## Implementação Realizada

### Banco de Dados Criado
- Arquivo: `biblioteca_arturtaborda.db`

### Estrutura da Tabela `livros`
```sql
CREATE TABLE livros (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    titulo TEXT NOT NULL,
    autor TEXT NOT NULL,
    ano_publicacao INTEGER,
    isbn TEXT UNIQUE
);
```

### Dados Inseridos
- Pride and Prejudice | Jane Austen | 1813 | 978-0486284736
- The Great Gatsby | F. Scott Fitzgerald | 1925 | 978-0743273565
- 1984 | George Orwell | 1949 | 978-0451524935
- The Catcher in the Rye | J.D. Salinger | 1951 | 978-0316769488
- To Kill a Mockingbird | Harper Lee | 1960 | 978-0061120084

### Teste de Restrição UNIQUE
Tentativa de inserir ISBN duplicado resultou em erro: "UNIQUE constraint failed: livros.isbn"

### Consulta Executada
```sql
SELECT titulo, autor FROM livros ORDER BY ano_publicacao;
```
Resultado:
- Pride and Prejudice | Jane Austen
- The Great Gatsby | F. Scott Fitzgerald
- 1984 | George Orwell
- The Catcher in the Rye | J.D. Salinger
- To Kill a Mockingbird | Harper Lee

### Git Commits
- Commit realizado: "feat: estrutura e dados da biblioteca finalizados"
- Push para branch `FabioIndex/2jat1`

----------

 Regras de Ouro (O que será avaliado):

-   **Sintaxe:**  O uso correto do  `;`  ao final dos comandos.
-   **Tipagem:**  Se você usou  `INTEGER`,  `TEXT`  ou  `REAL`  nos lugares certos.
-   **Restrições:**  Se a coluna  `isbn`  realmente impede duplicatas e se o  `titulo`  não aceita valores nulos.
-   **Persistência:**  O arquivo  `.db`  deve aparecer no seu GitHub após o push.
