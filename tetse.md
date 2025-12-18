Para fazer com que o servidor Express reinicie automaticamente ao salvar alterações, você pode utilizar o recurso nativo do Node.js ou ferramentas de terceiros como o Nodemon. 

# 1. Usando o recurso nativo (Node.js 18.11+)
Desde as versões mais recentes, o Node.js possui um modo de observação embutido que elimina a necessidade de pacotes externos para projetos simples. 

- Comando: No terminal, execute o servidor com a flag --watch :
  ```bash
  node --watch app.js
  ```

(Substitua app.js pelo nome do seu arquivo principal). 

# 2. Usando o Nodemon (Recomendado para projetos maiores)
O Nodemon é a ferramenta mais utilizada pela sua robustez e recursos avançados, como ignorar pastas específicas ou monitorar extensões variadas. 

- Instalação: Recomenda-se instalá-lo como dependência de desenvolvimento:
  ```bash
  npm install --save-dev nodemon
  ```
- Como usar:
  1. No arquivo package.json, adicione um script na seção "scripts" :
     ```json
     "scripts": {
        "dev": "nodemon app.js"
     }
     ```

  2. Inicie o servidor com o comando:
     ```bash
     npm run dev
     ```

Para quem utiliza TypeScript, o Nodemon combinado com o ts-node continua sendo uma escolha comum em 2025 para garantir reinicializações rápidas e consistentes.
