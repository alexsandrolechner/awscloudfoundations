# Aws Cloud Foundations

# Projeto Website Estático com CI/CD na AWS

Este repositório contém um website estático em HTML e demonstra como configurar uma pipeline de CI/CD utilizando GitHub Actions para fazer o deploy automático para um bucket S3 na AWS.

## Estrutura do Repositório

- **.github/workflows**: Contém os arquivos de workflow do GitHub Actions (ex.: `main.yml`) que orquestram o processo de deploy.
- **website**: Pasta que contém os arquivos do site (HTML, CSS, JS e imagens).
- **.gitignore**: Define os arquivos e pastas que não serão versionados.
- **README.md**: Este arquivo, com informações importantes sobre o projeto e o fluxo de deploy.

## Pontos Importantes

1. **Deploy Automático com GitHub Actions**

   - Sempre que houver um push para o branch `main`, o workflow é acionado.
   - O workflow faz o checkout do repositório, remove pastas desnecessárias (como `.git` e `.github`) e sincroniza apenas a pasta `website` com o bucket S3.
   - O deploy é feito utilizando a ação `jakejarvis/s3-sync-action` sem aplicar ACLs, garantindo compatibilidade com buckets com Object Ownership configurado como "Bucket owner enforced".

2. **Configuração do Bucket S3 para Hospedagem de Site Estático**

   - O bucket S3 foi configurado para hospedar um site estático.
   - Foi habilitada a opção de "Static website hosting", definindo o documento de índice (ex.: `index.html`) e, se necessário, o documento de erro.
   - Uma política de bucket foi aplicada para permitir acesso público de leitura aos arquivos.

3. **Variáveis e Segredos do AWS**

   - Os segredos (como `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION` e `S3_BUCKET`) estão configurados em um Environment no GitHub, e são injetados no workflow durante a execução.

4. **.gitignore**
   - O arquivo `.gitignore` garante que arquivos desnecessários (como logs, pastas de dependências, arquivos de sistema e configurações de IDE) não sejam versionados.

## Instruções para Alunos

- **Entender o Pipeline:**  
  Estudem como o GitHub Actions é configurado no arquivo de workflow para automatizar o processo de deploy. Observem os passos de checkout, limpeza do repositório e sincronização com o S3.

- **Configurar o Bucket S3:**  
  Verifiquem as configurações do bucket S3 para hospedagem de site estático e a política de acesso público.

- **Ajustar o Repositório:**  
  Caso necessário, modifiquem a estrutura ou os arquivos do website na pasta `website` e observem como o deploy é refletido automaticamente após cada push para o branch `main`.

Este repositório é um exemplo prático de como integrar GitHub e AWS para automatizar o deploy de um site estático. Aproveitem para explorar e ajustar conforme as necessidades dos seus projetos!
