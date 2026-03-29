# Bot Advocacia - Assistente Virtual e Fluxo de Atendimento

Este projeto consiste em uma infraestrutura completa e conteinerizada para um assistente virtual focado em escritorios de advocacia. O sistema utiliza o Typebot para a criacao e gerenciamento do fluxo de conversacao e a Evolution API para a integracao com plataformas de mensageria, como o WhatsApp.

## Tecnologias Utilizadas

- Docker & Docker Compose: Orquestracao e conteinerizacao dos servicos.
- PostgreSQL: Banco de dados relacional para armazenar as informacoes da plataforma.
- Typebot (Builder e Viewer): Ferramenta visual open-source para criacao de fluxos de chat avancados.
- Evolution API: API para integracao de instancias de WhatsApp de forma simplificada e direta.

## Funcionalidades do Fluxograma

O arquivo de fluxo exportado (`typebot-export-template-advocacia.json`) contem uma arvore de decisao inteligente para a triagem automatica de contatos:

1. Contratacao e Agendamento: Informa valores de consulta, coleta dados para agendamentos (presencial ou online) e solicita resumo do caso.
2. Atendimento Corporativo (PJ): Atendimento e triagem diferenciada para empresas.
3. Andamento de Processos: Direcionamento para clientes ativos, solicitando nome completo e numero do processo.
4. Mentoria Juridica: Captacao de dados e principais dificuldades de advogados interessados em mentoria pratica.
5. Parcerias e Palestras: Recepcao de propostas para eventos, detalhando tema, data e publico-alvo.

## Instalacao e Uso

### Pre-requisitos

Certifique-se de ter o Docker e o Docker Compose instalados no seu ambiente de hospedagem ou maquina local.

### Passo a Passo

1. Preparacao do Ambiente
   Faca uma copia do arquivo `.env.example` e renomeie-a para `.env` na raiz do projeto.
   ```bash
   cp .env.example .env
   ```

2. Configuracao das Variaveis
   Abra o arquivo `.env` e preencha com as suas senhas seguras, URLs e chaves de API (incluindo o Client ID e Secret do GitHub para autenticacao do Typebot).

3. Execucao dos Servicos
   Suba os conteineres em segundo plano executando:
   ```bash
   docker-compose up -d
   ```

4. Importacao do Fluxo
   - Acesse o painel do Typebot Builder (por padrao configurado na porta `8080`, ex: `http://localhost:8080`).
   - Realize o login via GitHub.
   - Crie um novo bot e utilize a funcao de importacao para carregar o arquivo `.json` incluso neste repositorio.

## Seguranca e Boas Praticas

- As pastas de volumes locais (`db-data` e `evolution_data`) e o arquivo `.env` ja estao devidamente mapeados no `.gitignore`.
- O arquivo `.env` atua como a unica fonte da verdade para segredos do sistema. Nunca realize commits deste arquivo em repositorios publicos, pois ele contem credenciais de banco de dados e chaves de criptografia.

## Licenca

Este projeto esta sob a licenca MIT. Veja o arquivo LICENSE para mais detalhes.

---
Desenvolvido como demonstracao de automacao de atendimento e arquitetura de microsservicos com Docker.