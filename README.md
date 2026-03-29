# Bot Advocacia - Assistente Virtual e Fluxo de Atendimento

Este projeto consiste em uma infraestrutura completa e conteinerizada para um assistente virtual focado em escritórios de advocacia. O sistema utiliza o Typebot para a criação e gerenciamento do fluxo de conversação e a Evolution API para a integração com plataformas de mensageria, como o WhatsApp.

## Tecnologias Utilizadas

- **Docker e Docker Compose**: Orquestração e conteinerização dos serviços.
- **PostgreSQL 16**: Banco de dados relacional para persistência de dados da plataforma.
- **Typebot (Builder e Viewer)**: Engine visual para criação de fluxos de chat avançados.
- **Evolution API v1.8.2**: Gateway para integração de instâncias de WhatsApp de forma simplificada.

## Funcionalidades do Fluxograma

O arquivo de fluxo exportado (`typebot-export-template-advocacia.json`) contém uma árvore de decisão para a triagem automática de contatos. Um diferencial técnico deste fluxo é a implementação de **menus baseados em resposta numérica**, garantindo compatibilidade total entre diferentes versões do WhatsApp (Web e Mobile) e evitando falhas comuns em botões interativos.

1. **Contratação e Agendamento**: Coleta de dados para agendamentos presenciais ou online e resumo do caso jurídico.
2. **Atendimento Corporativo (PJ)**: Fluxo específico para triagem de empresas.
3. **Andamento de Processos**: Direcionamento para clientes ativos, solicitando número do processo e identificação.
4. **Mentoria Jurídica**: Captação de leads para advogados interessados em mentoria prática.
5. **Parcerias e Palestras**: Recepção de propostas detalhando tema, data e público-alvo.

## Instalação e Uso

### Pré-requisitos

Certifique-se de ter o Docker e o Docker Compose instalados no seu ambiente de hospedagem (VPS) ou máquina local.

### Passo a Passo

1. **Preparação do Ambiente**
   Crie uma cópia do arquivo `.env.example` e renomeie-a para `.env` na raiz do projeto.
   ```bash
   cp .env.example .env
   ```

2. **Configuração das Variáveis**
   Abra o arquivo `.env` e preencha com as suas senhas seguras, URLs e chaves de API (incluindo o Client ID e Secret do GitHub para autenticação do Typebot).

3. **Execução dos Serviços**
   Suba os contêineres em segundo plano executando:
   ```bash
   docker-compose up -d
   ```

4. **Acesso aos Painéis**
   - Typebot Builder: Por padrão configurado na porta `8080`, ex: `http://localhost:8080`.
   - Typebot Viewer: Por padrão configurado na porta `8081`, ex: `http://localhost:8081`.
   - Evolution Manager: Por padrão configurado na porta `8082`, ex: `http://localhost:8082`.

5. **Importação do Fluxo**
   - Acesse o Typebot Builder.
   - Realize o login via GitHub.
   - Crie um novo bot e utilize a função de importação para carregar o arquivo `.json` incluso neste repositório.

## Segurança e Boas Práticas

- As pastas de volumes locais (`db-data` e `evolution_data`) e o arquivo `.env` já estão devidamente mapeados no `.gitignore`.
- O arquivo `.env` atua como a única fonte da verdade para segredos do sistema. Nunca realize commits deste arquivo em repositórios públicos, pois ele contém credenciais de banco de dados e chaves de criptografia.

## Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.

---
Desenvolvido como demonstração de automação de atendimento e arquitetura de microsserviços com Docker.