# Biblioteca Digital: Arquitetura Serverless na AWS


### 1. Descrição da Arquitetura:
   
  Esta solução implementa uma arquitetura serverless na AWS para gerenciar um sistema de armazenamento e catalogação de livros digitais (PDFs).
  Quando um usuário faz upload de um livro em PDF, uma função Lambda é acionada para extrair texto e metadados (autor, título, número de páginas) e gerar um índice pesquisável, que é armazenado no DynamoDB.
  
  O arquivo original é mantido em um bucket S3 final, e a aplicação da biblioteca (hospedada em uma instância EC2) permite que os usuários realizem buscas inteligentes por autor, título ou palavra-chave.
  <img width="646" height="521" alt="image" src="https://github.com/user-attachments/assets/0e323e9a-da7f-4330-872f-f522b74020c6" />

### 2. Arquitetura:
 Componentes da Arquitetura

 - Amazon S3 (Bucket de Entrada) → Recebe os arquivos PDF enviados pelos usuários.

 - AWS Lambda → Processa os PDFs, extrai texto e metadados e gera o índice.

 - Amazon CloudWatch → Monitora e registra logs do Lambda.

 - Amazon DynamoDB → Armazena o catálogo de livros e os índices de pesquisa.

 - Amazon S3 (Bucket de Saída) → Armazena os PDFs finais que farão parte da coleção da biblioteca.

 - Amazon EC2 → Hospeda a aplicação da biblioteca para consulta e busca de livros.

### 3. Fluxo de Processamento

 - O usuário faz upload de um PDF para o bucket de entrada (S3).

 - O evento de novo arquivo aciona a função Lambda.

 - A Lambda processa o PDF:

 - Extrai texto e metadados.

 - Cria um índice pesquisável.

 - Esse processo é monitorado via CloudWatch.

 - Salva informações no DynamoDB.

 - O PDF original é copiado para o bucket de saída (S3).

 - A aplicação em EC2 consulta o DynamoDB e permite buscas por autor, título ou palavra-chave.

### 4. Implementação

 - Criar buckets S3 (entrada e saída).

 - Desenvolver a função Lambda para:

      Extrair texto e metadados dos PDFs.
      
      Salvar dados no DynamoDB.
      
      Copiar PDFs para o bucket final.
      
      Configurar gatilho S3 → Lambda.

 - Habilitar CloudWatch Logs para monitoramento.

 - Criar tabela no DynamoDB para armazenar catálogo.

 - Configurar instância EC2 com aplicação da biblioteca.








