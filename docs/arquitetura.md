# Arquitetura do Sistema — Copiloto de Campo do Promotor

## 1. Visão Geral da Solução
O Copiloto de Campo atua como uma camada middleware de inteligência operacional que conecta a base de conhecimento corporativa (manuais, POPs, diretrizes de Trade) às interfaces móveis utilizadas pelos promotores no Ponto de Venda (PDV) [6, 7].

## 2. Componentes do Sistema e Status de Implementação

### Componentes Implementados / Testados em Protótipo
- **Camada de Conhecimento Rastreável (Gemini Notebook)**: Repositório central de documentos oficiais, vídeos educativos e normativas técnicas [2, 4, 5].
- **Motor de Ingestão e Indexação**: Processamento de arquivos PDF, URLs, áudios e vídeos com geração de trechos indexados [4-6].
- **Mecanismo de Busca Semântica e RAG**: Recuperação de passagens relevantes com geração de citações diretas aos documentos originais.
- **Interface Móvel de Consulta (Protótipo)**: Aplicação móvel para entrada de texto/voz e exibição de respostas estruturadas no PDV [7].

### Componentes em Desenvolvimento / Proposta de Integração
- **Barramento de Integração de TI (ITSM / ERP)**: Conexão planejada com sistemas ITSM (ex.: Service Manager/Jira) para abertura automática de chamados de escalonamento [1, 9, 16].
- **Leitor de Código de Barras / EAN**: Leitura de itens em gôndola para cruzamento direto com o cadastro do produto e plano de validade (Proposta em Validação) [4, 17].
- **Painel de Operações e Monitoramento (NOC / Dashboards)**: Monitoramento de métricas de consulta, taxa de resolutividade no PDV e indicadores de ruptura [1, 14, 16].

## 3. Fluxo de Informação
1. **Promotor** faz uma requisição por voz ou texto no aplicativo móvel [7].
2. **App Móvel** encaminha a requisição autenticada para o **Motor de IA**.
3. **Motor de IA** realiza busca semântica na **Base de Conhecimento Rastreável**.
4. **Base de Conhecimento** devolve os trechos e referências com maior similaridade semântica.
5. **Motor de IA** aplica as regras de governança (formatação de 5 blocos + verificação de evidências).
6. **App Móvel** exibe a orientação prática com indicação da fonte oficial e próximo passo [7].

## 4. Dependências Técnicas e Padrões
- **Modelos de Maturidade de Processos**: Alinhamento ao Modelo Corporativo de Processos de Software (MCPSE) da Embrapa para gestão de requisitos e controle de baseline [15].
- **Segurança da Informação e LGPD**: Atendimento às normas ABNT NBR ISO/IEC 27001 e NBR 22301, com restrição total à exposição de dados pessoais e segredos comerciais [5, 17, 18].
- **Monitoramento e SLA**: Adoção de métricas DEM/RUM e níveis de serviço alinhados às boas práticas de suporte de TI [1, 16].
