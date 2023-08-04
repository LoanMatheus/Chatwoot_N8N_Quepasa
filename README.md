## Instruções de Configuração do Projeto

Este guia fornece instruções detalhadas para configurar e executar o projeto. Certifique-se de seguir todos os passos cuidadosamente para garantir um funcionamento adequado.


## Passo 1: Baixar o Projeto

Clone o repositório do projeto em seu ambiente local:

```bash
git clone git@github.com:LoanMatheus/UPX.git
cd UPX
```

## Passo 2: Construir os Containers Docker

Use o seguinte comando para construir os containers Docker, sem iniciá-los:

```bash
docker-compose up --build --no-start
```

## 3. Preparar o Banco de Dados
Execute o seguinte comando para preparar o banco de dados do Chatwoot:

```bash
docker-compose run --rm rails bundle exec rails db:chatwoot_prepare
```
## 4. Corrigir Permissões (caso necessário)
Se ocorrerem erros durante a execução, pare o processo Docker e execute o seguinte comando para corrigir permissões:

```bash
sudo chmod -R 777 ./data/.n8n
```

## 5. Criar Contas de Usuário
Abra os seguintes URLs em seu navegador e crie uma conta em cada uma delas:

- [http://localhost:8080/](http://localhost:8080/)
- [http://localhost:8081/](http://localhost:8081/)
- [http://localhost:8084/](http://localhost:8084/)

## 6. Configurar Caixa de Entrada
Faça login em http://localhost:8080/ e crie uma caixa de entrada. Escolha a opção "API" e digite "http://" no campo de webhook.

## 7. Configurar Workflows no n8n
Faça login no n8n e carregue os workflows localizados na pasta /n8n, salvando-os com os nomes dos arquivos.

## 8. Instalar Nodes do n8n
Certifique-se de instalar os seguintes nodes no n8n:

- n8n-nodes-chatwoot
- n8n-nodes-quepasa

## 9. Adicionar Credenciais do PostgreSQL
Adicione as seguintes credenciais do PostgreSQL:

- Host: postgres
- Banco de Dados: chatwoot_production
- Usuário: postgres
- Senha: chatwoot

## 10. Configurar IDs dos Flows
Adicione os IDs dos fluxos nos workflows "ChatwootToQuepasa" e "QuepasaToChatwoot". Além disso, adicione seu email cadastrado no Quepasa ao node "QuepasaQrCode".

## 11. Habilitar os Fluxos
Certifique-se de habilitar os seguintes fluxos:

- ChatwootToQuepasa
- QuepasaToChatwoot
- QuepasaQrCode
- QuepasaAutomatic

## 12. Conectar Dispositivo via Chatwoot
Envie uma mensagem "/qrcode" para o contato "Quepasa Control" no Chatwoot para iniciar a conexão do dispositivo.

Agora seu projeto está configurado e pronto para ser usado. Siga essas instruções sempre que precisar configurar o ambiente.
