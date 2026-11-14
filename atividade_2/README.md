# Sistema Multiagente de Triagem de Manutenção Técnica Industrial

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lucasomx/agente-triagem-manutencao/blob/main/atividade_2/atividade_2_multiagente_manutencao.ipynb)

Projeto desenvolvido para a Atividade 2 da disciplina de Engenharia de Agentes e IA Agêntica.

O projeto amplia o agente desenvolvido na Atividade 1, implementando uma arquitetura multiagente com LangGraph para realizar a triagem inicial de solicitações de manutenção técnica industrial.

A solução distribui responsabilidades entre agentes especializados, que compartilham informações por meio de um estado comum e são coordenados por um agente supervisor.

## Arquitetura multiagente

O sistema é composto por quatro agentes:

- **SupervisorAgent** — coordena o fluxo de execução e determina qual especialista deve atuar em cada etapa.
- **OperationsAgent** — consulta dados dos equipamentos, histórico de manutenção e disponibilidade de equipes.
- **KnowledgeAgent** — recupera procedimentos técnicos e a política de prioridades, utilizando busca semântica com ChromaDB.
- **TriageAgent** — analisa as evidências reunidas pelos especialistas e produz uma proposta estruturada de triagem, com justificativas e encaminhamento sugerido.

O LangGraph é utilizado para definir os nós, as transições condicionais e o compartilhamento de informações entre os agentes.

A arquitetura inclui versões simuladas dos agentes que dependem do modelo de linguagem, permitindo validar o fluxo sem realizar chamadas à API.

## Tecnologias utilizadas

- Python e Jupyter Notebook;
- LangGraph para orquestração dos agentes;
- Google Gemini API para decisões e geração de triagem;
- ChromaDB para recuperação de documentos;
- Pandas para tratamento dos dados operacionais;
- Google Colab para execução do notebook.

## Execução no Google Colab

Clique no botão **Open in Colab** no início deste README.

O notebook instala as dependências necessárias e baixa os arquivos de dados do diretório `atividade_2` deste repositório quando eles não estiverem disponíveis no ambiente de execução.

### API Key

As demonstrações que utilizam o Gemini requerem uma chave da API.

No Google Colab, a chave pode ser configurada em **Secrets**, com o nome:

`GOOGLE_API_KEY`

Também é possível informá-la manualmente quando solicitado pelo notebook.

A chave não deve ser incluída diretamente no código nem armazenada neste repositório.

### Demonstrações opcionais

O notebook possui configurações que controlam a execução das demonstrações com chamadas reais ao Gemini:

```python
EXECUTAR_DEMO_MULTIAGENTE = False
EXECUTAR_DEMO_TRIAGE_ISOLADO = False
EXECUTAR_DEMOS_LEGADAS = False
```

As demonstrações ficam desativadas por padrão. Para executar uma delas, altere a opção correspondente para `True`.

A execução com Gemini depende da disponibilidade do serviço e dos limites de requisições aplicáveis à chave utilizada.

## Testes e validação

O notebook contém testes para verificar:

- consultas operacionais e recuperação documental;
- execução individual dos agentes especialistas;
- compartilhamento de informações entre os agentes;
- roteamento condicional e coordenação pelo SupervisorAgent;
- integração dos agentes no LangGraph;
- processamento de respostas JSON simuladas;
- tratamento de erros e condições de falha.

Os testes offline e as simulações da arquitetura multiagente foram executados com sucesso no VS Code e no Google Colab.

Nas tentativas de execução real do TriageAgent durante a validação no Colab, a API Gemini retornou erros HTTP 503 e 504, relacionados à indisponibilidade do modelo e ao prazo limite de resposta. Assim, a geração de uma triagem real pelo Gemini não foi confirmada nesses testes.

## Arquivos principais

- `atividade_2_multiagente_manutencao.ipynb` — notebook principal da Atividade 2;
- `equipamentos.csv` — cadastro e informações operacionais dos equipamentos;
- `historico_manutencao.csv` — histórico de ocorrências de manutenção;
- `equipes.csv` — disponibilidade das equipes;
- `procedimento_seguranca.txt` — orientações de segurança;
- `procedimento_mecanico.txt` — procedimentos mecânicos;
- `procedimento_eletrico.txt` — procedimentos elétricos;
- `politica_prioridades.txt` — critérios de priorização das solicitações.

## Observação

O sistema realiza triagem e apoio à decisão, utilizando informações operacionais e documentais. As recomendações produzidas não substituem a avaliação de profissionais responsáveis nem autorizam intervenções técnicas sem a devida verificação de segurança.