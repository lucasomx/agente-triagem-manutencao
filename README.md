# Agente de Triagem de Manutenção Técnica Industrial

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lucasomx/agente-triagem-manutencao/blob/main/atividade_1_agente_manutencao.ipynb)

Projeto desenvolvido para a Atividade 1 da disciplina de Engenharia de Agentes e IA Agêntica.

O projeto implementa um agente baseado em LLM para realizar a triagem inicial de solicitações de manutenção técnica industrial.

O agente utiliza um ciclo iterativo de decisão, ação e observação, com seleção dinâmica de ferramentas para consultar:

- dados cadastrais e operacionais de equipamentos;
- histórico de manutenção;
- disponibilidade de equipes;
- procedimentos e políticas recuperados por busca semântica.

A solução possui mecanismos básicos de robustez, incluindo validação de entradas, tratamento de erros, limite de iterações e retry com backoff para falhas transitórias da API.

## Execução no Google Colab

Clique no botão **Open in Colab** no início deste README.

O notebook instala automaticamente as dependências necessárias e baixa os arquivos de dados deste repositório quando eles não estiverem disponíveis localmente.

### API Key

A execução do agente requer uma chave da Gemini API.

No Google Colab, a chave pode ser adicionada em **Secrets** com o nome:

`GOOGLE_API_KEY`

Também é possível informá-la manualmente quando solicitado pelo notebook.

A chave da API não deve ser incluída no código nem armazenada neste repositório.

## Arquivos principais

- `atividade_1_agente_manutencao.ipynb` — notebook principal;
- `equipamentos.csv` — cadastro dos equipamentos;
- `historico_manutencao.csv` — histórico de ocorrências;
- `equipes.csv` — dados das equipes;
- `procedimento_seguranca.txt` — orientações de segurança;
- `procedimento_mecanico.txt` — procedimentos mecânicos;
- `procedimento_eletrico.txt` — procedimentos elétricos;
- `politica_prioridades.txt` — critérios de priorização.

## Observação

O agente realiza triagem e apoio à decisão. Ele não substitui avaliação técnica humana e não autoriza intervenções de manutenção.