## BookStack · KCS · n8n · RAG · Banco Vetorial (Qdrant) · Inteligência Artificial Generativa

| Campo | Valor |
|-------|-------|

| **Versão** | 5.0 |
| **Data** | Julho de 2026 |
| **Classificação** | Interno |
| **Organização** | Embrapa — Empresa Brasileira de Pesquisa Agropecuária |

### Histórico de Revisões

| Versão | Data | Descrição |
|--------|------|-----------|
| 1.0 | 2026 | Versão inicial (compilação de sessões de trabalho) |
| 2.0 | Julho 2026 | Primeira consolidação e remoção de duplicidades |
| 3.0 | Julho 2026 | Reestruturação completa, eliminação de redundâncias, padronização editorial e inclusão de novos elementos |
| 4.0 | Julho 2026 | Revisão geral e adaptação da base de conhecimento para a nova estrutura de 6 Estantes (Corporativo vs. Unidades) |
| 5.0 | Julho 2026 | Inclusão do n8n como camada de orquestração, padronização "banco vetorial (Qdrant)", ajuste da Regra 80/20 e reforço do escopo exclusivo de TI |

---

## Sumário

1. [Capítulo 1 — Introdução](#capítulo-1--introdução)
2. [Capítulo 2 — Princípios Fundamentais](#capítulo-2--princípios-fundamentais-da-gestão-do-conhecimento)
3. [Capítulo 3 — Arquitetura da Informação](#capítulo-3--arquitetura-da-informação)
4. [Capítulo 4 — Modelo Corporativo de Metadados e Taxonomia](#capítulo-4--modelo-corporativo-de-metadados-e-taxonomia)
5. [Capítulo 5 — Metodologia KCS e Governança Editorial](#capítulo-5--metodologia-kcs-e-governança-editorial)
6. [Capítulo 6 — Governança Corporativa e Descentralização](#capítulo-6--governança-corporativa-e-descentralização)
7. [Capítulo 7 — Padrão Editorial e Redação de Artigos](#capítulo-7--padrão-editorial-e-redação-de-artigos)
8. [Capítulo 8 — Templates Corporativos de Artigos](#capítulo-8--templates-corporativos-de-artigos)
9. [Capítulo 9 — Arquitetura Técnica de Recuperação e IA](#capítulo-9--arquitetura-técnica-de-recuperação-e-ia-rag)
10. [Capítulo 10 — Roadmap de Implementação e Modelo de Maturidade](#capítulo-10--roadmap-de-implementação-e-modelo-de-maturidade)
11. [Considerações Finais](#considerações-finais)
12. [Anexo A — Dicionário Corporativo e Vocabulário Controlado](#anexo-a--dicionário-corporativo-e-vocabulário-controlado)
13. [Anexo B — Referência de Metadados e Payload](#anexo-b--referência-de-metadados-e-payload)
14. [Anexo C — Glossário de Siglas](#anexo-c--glossário-de-siglas)
15. [Referências Bibliográficas](#referências-bibliográficas)

---

## Sumário Executivo

A Embrapa enfrenta desafios comuns a organizações de grande porte com estrutura descentralizada: conhecimento técnico disperso em múltiplos sistemas, duplicidade de informações, dependência de especialistas e dificuldade em localizar soluções já existentes.

Este documento estabelece a **Arquitetura Corporativa da Base de Conhecimento** — um modelo integrado que transforma a gestão do conhecimento de TI da Embrapa por meio de cinco pilares:

1. **Organização estruturada** no BookStack, com hierarquia de Estantes, Livros, Capítulos e Páginas orientada a domínios de conhecimento.
2. **Metodologia KCS** (Knowledge-Centered Service) adaptada à realidade da Embrapa, promovendo a captura contínua de conhecimento durante a operação diária.
3. **Taxonomia e metadados padronizados**, separando a estrutura organizacional dos marcadores de qualificação para reduzir redundâncias e facilitar a governança.
4. **Arquitetura de Recuperação Aumentada por Geração (RAG)**, integrando pipelines de indexação orquestrados pelo n8n (plataforma de automação de workflows), bancos vetoriais (Qdrant) e modelos de linguagem para busca semântica e assistentes inteligentes.
5. **Governança editorial e descentralização**, estruturada em **6 Estantes independentes** que dividem o escopo Corporativo (Embrapa) e Local (Unidades) para cada público-alvo (Suporte ao Usuário, Operação de TI e Administração de TI), operacionalizando a Regra 80/20 de proporção de conhecimento.

A implementação está organizada em **oito fases progressivas**, desde a infraestrutura básica até agentes inteligentes e melhoria contínua, com indicadores de maturidade para acompanhamento.

O resultado esperado é uma Base de Conhecimento que funcione simultaneamente como repositório para pessoas, fonte de dados para mecanismos de busca, acervo semântico para IA e plataforma de melhoria contínua — independente de fornecedores tecnológicos específicos.

---

# Capítulo 1 — Introdução

## 1.1 Objetivo

A transformação digital das organizações ampliou significativamente a quantidade de informações produzidas diariamente. Procedimentos técnicos, normas, soluções de incidentes, projetos, arquiteturas, manuais e decisões operacionais são constantemente criados, revisados e compartilhados entre diferentes equipes.

Apesar desse grande volume de conhecimento, muitas organizações ainda enfrentam desafios recorrentes:

* duplicidade de informações;
* documentos desatualizados;
* conhecimento disperso em múltiplos sistemas;
* dependência de especialistas;
* dificuldade em localizar rapidamente a informação correta;
* baixa reutilização das soluções já existentes.

No contexto da Embrapa, esse desafio torna-se ainda mais relevante devido à existência de uma estrutura organizacional distribuída, composta por uma unidade central e quarenta e quatro Unidades Descentralizadas, cada uma com características operacionais próprias.

A Base de Conhecimento Corporativa proposta neste documento foi concebida para enfrentar esse cenário por meio de uma arquitetura orientada ao conhecimento, construída sobre o BookStack e fundamentada nos princípios do Knowledge-Centered Service (KCS), complementados por tecnologias de Recuperação Aumentada por Geração (RAG), bancos vetoriais (Qdrant) e Inteligência Artificial Generativa.

O objetivo não é apenas armazenar documentos, mas transformar conhecimento organizacional em um ativo reutilizável, pesquisável e continuamente aprimorado.

## 1.2 Escopo

Esta arquitetura define as diretrizes para:

* organização da Base de Conhecimento no BookStack;
* padronização da taxonomia corporativa;
* estruturação de Estantes, Livros, Capítulos e Páginas;
* utilização de marcadores (tags) e metadados;
* produção de artigos seguindo a metodologia KCS;
* preparação do conteúdo para sistemas RAG;
* integração com bancos vetoriais (Qdrant);
* consumo por assistentes virtuais e agentes inteligentes;
* governança editorial;
* manutenção contínua da qualidade do conhecimento.

## 1.3 Público-alvo

Este documento destina-se aos seguintes públicos:

| Público | Objetivo |
|---------|----------|
| Equipe de Governança de TI | Definir padrões corporativos |
| Service Desk | Produzir conhecimento reutilizável |
| Especialistas Técnicos | Registrar procedimentos, arquiteturas e soluções |
| Gestores | Estabelecer governança do conhecimento |
| Equipe de IA | Implementar pipelines de indexação e RAG |
| Desenvolvedores | Integrar sistemas à Base de Conhecimento |

## 1.4 Visão Geral: Muito Além de uma Wiki

Embora o BookStack seja frequentemente utilizado como uma Wiki corporativa, nesta arquitetura ele assume um papel muito mais amplo. A Base de Conhecimento passa a ser considerada uma plataforma estratégica composta por quatro camadas complementares:

```text
Pessoas
            │
            ▼
  Base de Conhecimento (BookStack)
            │
            ▼
  Orquestração (n8n) — Acesso à API do BookStack
            │
            ▼
  Pipeline de Conhecimento (Parser + Chunking + IA)
            │
            ▼
  Banco Vetorial (Qdrant)
            │
            ▼
  Chatbots e Agentes de IA
```
Cada camada possui responsabilidades específicas e independentes, permitindo evolução contínua sem comprometer as demais.

## 1.5 Os Quatro Consumidores do Conhecimento

Todo artigo produzido deverá atender simultaneamente a quatro consumidores distintos:

| Consumidor | Necessidade |
|------------|-------------|
| **Ser humano** | Respostas claras, objetivas e organizadas; navegação intuitiva |
| **Mecanismo de busca** | Estrutura consistente para localizar rapidamente documentos relevantes |
| **Banco vetorial** | Conteúdo semanticamente bem organizado para gerar embeddings de qualidade |
| **Inteligência Artificial** | Documentos granulares, bem contextualizados e ricos em significado para respostas precisas |

Essa arquitetura busca atender simultaneamente aos quatro consumidores.

---

# Capítulo 2 — Princípios Fundamentais da Gestão do Conhecimento

## 2.1 Os Doze Princípios Corporativos

Toda a Base de Conhecimento será construída obedecendo aos doze princípios descritos a seguir, que estabelecem as diretrizes permanentes para a evolução da arquitetura corporativa da gestão do conhecimento da Embrapa.

### Princípio 1 — O Conhecimento de TI é um Ativo Corporativo

O conhecimento de TI registrado não pertence ao autor, à equipe ou à unidade responsável por sua criação. Todo conteúdo produzido passa a integrar o patrimônio intelectual da organização, devendo ser registrado, preservado, compartilhado, reutilizado e continuamente aprimorado. Nenhum conhecimento crítico deverá permanecer exclusivamente na memória de indivíduos ou equipes.

### Princípio 2 — Organização Orientada ao Domínio

A organização da informação no BookStack deverá refletir o domínio funcional do conhecimento (ex: Livro: *Google Workspace*, Capítulos: *Google Drive*, *Google Meet*) e não o tipo de documento (ex: Livro: *Procedimentos*, *Incidentes*, *Tutoriais*, *FAQ*). Os tipos de conteúdo serão representados por marcadores (tags), preservando a proximidade semântica entre artigos relacionados ao mesmo assunto.

### Princípio 3 — Atomicidade e Foco Único

Cada página deverá possuir um único objetivo claramente definido, respondendo a uma única necessidade, problema ou pergunta. Quanto menor for o escopo da página, maior será sua precisão na recuperação semântica e sua capacidade de reutilização. Deve-se evitar manuais longos e generalistas que concentrem diversos assuntos distintos.

### Princípio 4 — Separação de Responsabilidades

A arquitetura distingue claramente a **estrutura da informação** (que representa a localização hierárquica do artigo no BookStack) dos **marcadores** (que qualificam e caracterizam o conhecimento, como tipo, produto, versão ou criticidade). Essa separação evita redundâncias de classificação e facilita a indexação inteligente para a IA.

### Princípio 5 — Estrutura antes da Tecnologia

A organização do conhecimento deve ser concebida de forma independente das ferramentas tecnológicas utilizadas. A arquitetura lógica deve ser robusta o suficiente para permitir a substituição de plataformas tecnológicas sem que isso exija a reestruturação do acervo de conhecimento ou a perda do patrimônio intelectual produzido.

### Princípio 6 — Otimização Dual

A Base de Conhecimento é otimizada simultaneamente para consumo humano e processamento por sistemas de IA. Isso significa organizar as páginas de forma intuitiva para a leitura e navegação das pessoas e, ao mesmo tempo, de maneira semanticamente rica e consistente para viabilizar embeddings, pipelines RAG e respostas precisas de modelos de linguagem.

### Princípio 7 — Simplicidade por Padrão

A arquitetura de informação e os fluxos editoriais devem privilegiar modelos simples e intuitivos. Estruturas excessivamente complexas reduzem a qualidade da documentação, desestimulam a contribuição voluntária e dificultam a sustentabilidade da base. Sempre que existirem múltiplos caminhos possíveis, adota-se o mais simples que atenda aos requisitos.

### Princípio 8 — Metadados Mínimos e Automatizados

Os autores devem preencher manualmente apenas os metadados editoriais que a estrutura da base não consegue expressar. Todas as demais informações (como estante, livro, autor, data de criação, etc.) devem ser inferidas ou extraídas automaticamente via API pelo pipeline de indexação. Isso reduz erros de taxonomia e simplifica o processo de escrita.

### Princípio 9 — Governança Editorial Contínua

A Base de Conhecimento não é um repositório estático. A sua qualidade depende de um processo permanente de revisão, atualização e saneamento. Artigos obsoletos, inconsistentes ou duplicados devem ser identificados, revisados ou arquivados de forma rotineira, garantindo a confiabilidade da informação.

### Princípio 10 — Conhecimento Baseado em Evidências

Todo artigo publicado na base deve representar conhecimento técnico validado, fundamentado em evidências e soluções homologadas. Hipóteses sem validação prática, opiniões pessoais ou procedimentos não homologados não devem compor a base oficial corporativa.

### Princípio 11 — Inteligência Artificial como Amplificadora

A Inteligência Artificial e os chatbots não substituem a Base de Conhecimento, mas ampliam sua utilidade e acessibilidade. Toda resposta gerada por assistentes virtuais ou agentes inteligentes baseados em RAG deve estar estritamente fundamentada em artigos validados e oficialmente publicados na base corporativa.

### Princípio 12 — Contextualização e Regra 80/20

A arquitetura do conhecimento de TI deve contemplar a realidade descentralizada da Embrapa, priorizando o conhecimento corporativo comum (80%) e tratando particularidades regionais ou de unidades locais (20%) de forma estruturada. Isso é alcançado dividindo a Base de Conhecimento em estantes lógicas segregadas por público (Suporte ao Usuário, Operação de TI, Administração de TI) e por escopo (Embrapa vs. Unidades), totalizando **6 Estantes Corporativas** que evitam a duplicação ou fragmentação das informações comuns.

## 2.2 Manifesto da Gestão do Conhecimento

A implantação de uma Arquitetura Corporativa de Gestão do Conhecimento representa uma transformação organizacional. Mais do que implantar uma plataforma tecnológica, trata-se de estabelecer uma cultura em que o conhecimento seja produzido, compartilhado, reutilizado e continuamente aperfeiçoado.

A metodologia KCS fornece os processos para capturar e evoluir esse conhecimento. O BookStack oferece a estrutura para organizá-lo. A taxonomia e os metadados garantem sua consistência. O RAG e os bancos vetoriais (Qdrant) ampliam sua recuperação. Os modelos de linguagem e agentes inteligentes potencializam sua aplicação.

Entretanto, nenhuma dessas tecnologias substitui a necessidade de governança, colaboração e compromisso institucional.

A arquitetura proposta foi concebida para ser:

* **escalável**, acompanhando o crescimento da organização;
* **modular**, permitindo a evolução independente de seus componentes;
* **interoperável**, integrando-se a sistemas como ITSM, CMDB, ITAM e plataformas de IA;
* **independente de fornecedores**, preservando o conhecimento diante da evolução tecnológica;
* **centrada no conhecimento**, reconhecendo que o verdadeiro patrimônio da organização não está nas ferramentas, mas na experiência acumulada de suas pessoas.

Ao adotar esta arquitetura, a organização estabelece as bases para transformar conhecimento em capacidade operacional, inovação e continuidade dos serviços.

---

# Capítulo 3 — Arquitetura da Informação

## 3.1 Objetivos

A arquitetura da informação define a forma como o conhecimento corporativo será organizado, armazenado, localizado e reutilizado. Nesta proposta, a organização da Base de Conhecimento não foi concebida apenas para facilitar a navegação humana — ela também foi projetada para atender aos requisitos de recuperação semântica, geração de embeddings e consumo por sistemas de Inteligência Artificial.

Toda a estrutura foi construída para responder simultaneamente a cinco objetivos:

* facilitar a localização da informação pelos usuários;
* reduzir a duplicidade de conteúdo;
* favorecer a reutilização do conhecimento;
* simplificar a governança editorial;
* otimizar a recuperação de contexto pelos modelos de IA.

## 3.2 Hierarquia Oficial do BookStack

A arquitetura corporativa adota quatro níveis hierárquicos, cada um com um propósito distinto:
```text
Estante → Livro → Capítulo → Página
```
A organização deverá obedecer aos seguintes princípios:

* separar conhecimento por público-alvo (Estantes);
* organizar Livros por domínio de conhecimento;
* organizar Capítulos por domínio funcional;
* utilizar Páginas como unidades atômicas de conhecimento;
* utilizar marcadores apenas para qualificar o conteúdo.

Nenhum desses princípios deverá ser violado sem aprovação da Governança da Base de Conhecimento.

## 3.3 Separação entre Estrutura e Classificação

Um dos pilares desta arquitetura consiste na separação clara entre **estrutura** e **classificação**. A estrutura representa **onde** o conhecimento está organizado. Os marcadores representam **o que** aquele conhecimento é. Misturar esses dois conceitos gera redundância, dificulta a manutenção da base e reduz a qualidade da recuperação semântica.

**A estrutura** organiza o conhecimento de forma hierárquica (Estante > Livro > Capítulo > Página), onde cada nível possui uma responsabilidade específica.

**Os marcadores** não organizam documentos — eles qualificam documentos. Exemplo: `tipo=procedimento`, `versao=17`, `criticidade=alta`. Nenhum desses atributos altera a localização do artigo dentro do BookStack.

## 3.4 Estantes Corporativas

As estantes representam o mais alto nível de organização. Sua função é separar grandes conjuntos de conhecimento de acordo com seu público-alvo (Consumidores) e o escopo de atuação (Corporativo/Embrapa ou Local/Unidades). Esta arquitetura define seis estantes corporativas principais:

| Estante | Público-Alvo | Escopo / Finalidade | Gestão do Conhecimento |
| :--- | :--- | :--- | :--- |
| **📚 Embrapa - Suporte ao Usuário** | Todos os colaboradores | Autoatendimento de ferramentas e sistemas corporativos comuns | Central (Sede / Gestão de Processos) |
| **📚 Unidades - Suporte ao Usuário** | Usuários de unidades específicas | Particularidades locais de autoatendimento das 44 unidades | Descentralizada (TI da respectiva Unidade) |
| **📚 Embrapa - Operação de TI** | Analistas de TI (Sede/Unidades) | Documentação técnica corporativa, infraestrutura e runbooks globais | Co-criada (Nível corporativo) |
| **📚 Unidades - Operação de TI** | Analistas de TI local | Particularidades de infraestrutura, redes e servidores locais da Unidade | Descentralizada (TI da respectiva Unidade) |
| **📚 Embrapa - Administração de TI** | Gestores de TI e Segurança | Governança, normativas, planejamento estratégico e contratos globais | Sede (Secretaria de TI) |
| **📚 Unidades - Administração de TI** | Chefes de TI local e Diretores | Inventários locais, contratos de TI locais e planos de contingência | Descentralizada (Chefia de TI da Unidade) |

Essa organização permite aplicar políticas distintas de acesso, ciclo de vida do conhecimento e indexação para IA (RAG).

### 📚 Estante: Embrapa - Suporte ao Usuário
**Finalidade:** Disponibilizar conhecimento destinado ao autoatendimento de ferramentas de uso comum por todos os colaboradores da Embrapa.
**Características:** Linguagem simples e acessível, guias passo a passo, foco em produtividade do usuário final e FAQ. É a principal fonte de conhecimento para o chatbot do Portal de Serviços corporativo.
**Exemplos de Livros:** Google Workspace, VPN Corporativa, Portal de Serviços (TOPdesk), Wi-Fi Corporativo, MFA.

### 📚 Estante: Unidades - Suporte ao Usuário
**Finalidade:** Armazenar guias de autoatendimento contendo particularidades geográficas ou operacionais específicas das 44 unidades.
**Características:** Organizada com um livro para cada unidade (ex: `📖 Embrapa Cerrados - Suporte ao Usuário`), contendo ramais locais, particularidades de impressão local, regras locais de acesso físico ou agendamento de recursos locais.
**Exemplos de Livros:** Embrapa Gado de Corte, Embrapa Cerrados, Embrapa Trigo.

### 📚 Estante: Embrapa - Operação de TI
**Finalidade:** Armazenar documentação de nível técnico para as equipes de suporte e infraestrutura global de toda a Embrapa.
**Características:** Linguagem técnica avançada, procedimentos operacionais detalhados, diagramas de arquitetura global, runbooks de sistemas centrais e guias de troubleshooting.
**Exemplos de Livros:** PostgreSQL Corporativo, Docker e Containers, Configuração do TOPdesk, Servidores Linux, Redes & Segurança.

### 📚 Estante: Unidades - Operação de TI
**Finalidade:** Permitir que as equipes técnicas locais documentem a infraestrutura de TI específica de suas unidades.
**Características:** Organizada com um livro por unidade (ex: `📖 TI - Embrapa Cerrados`), armazenando layouts de racks locais, configurações de switches e roteadores da unidade, rotinas de backups locais e contratos de links de internet locais.
**Exemplos de Livros:** TI - Embrapa Gado de Corte, TI - Embrapa Cerrados, TI - Embrapa Tabuleiros Costeiros.

### 📚 Estante: Embrapa - Administração de TI
**Finalidade:** Reunir documentos estratégicos de governança e conformidade de TI em nível nacional.
**Características:** Acesso restrito a gestores e assessores da Secretaria de TI (SIT). Contém as políticas de segurança da informação (PSI), planejamentos estratégicos (PETI/PDTIC) e gestão de contratos globais.
**Exemplos de Livros:** Governança, Políticas & Normas, Planejamento Estratégico, Arquitetura Corporativa de Sistemas.

### 📚 Estante: Unidades - Administração de TI
**Finalidade:** Concentrar a documentação de gestão local, inventários físicos e planos locais de resposta a emergências de cada unidade.
**Características:** Acesso restrito a diretores locais, chefes de TI local (COTIs) e assessores locais.
**Exemplos de Livros:** Gestão TI - Embrapa Gado de Corte, Gestão TI - Embrapa Cerrados.

## 3.5 Livros

Os Livros representam **domínios de conhecimento**. Um Livro deve corresponder a um assunto claramente identificável, permanente e consolidado. Nunca deve representar um procedimento, um incidente ou um tipo de documento — esses conceitos pertencem às Páginas e serão qualificados por marcadores.

**Exemplos adequados:** Docker, PostgreSQL, Google Workspace, TOPdesk, Linux, MongoDB, VPN, Redes, Segurança da Informação.

**Exemplos inadequados:** Incidentes, Procedimentos, FAQ, Tutoriais. Esses representam tipos de conteúdo, não domínios de conhecimento.

## 3.6 Capítulos

Os Capítulos representam **domínios funcionais** dentro do assunto tratado pelo Livro. Em versões anteriores da proposta, os capítulos eram utilizados para separar tipos de documentos. Após análise dos requisitos do KCS e dos mecanismos de recuperação semântica, esse modelo foi substituído por uma organização orientada ao domínio do conhecimento. Essa mudança aproxima artigos relacionados, melhora a navegação e aumenta a eficiência dos embeddings.

**Exemplo — Livro PostgreSQL:**
```text
Instalação | Arquitetura | Administração | Usuários e Permissões
Backup e Recuperação | Segurança | Performance | Replicação
Monitoramento | Integrações | Boas Práticas | Particularidades das Unidades
```
**Exemplo — Livro Docker:**
```text
Instalação | Arquitetura | Containers | Volumes | Redes | Imagens
Docker Compose | Segurança | Monitoramento | Backup
Integrações | Boas Práticas | Particularidades das Unidades
```
**Exemplo — Livro Google Workspace:**
```text
Primeiros Passos | Conta Google | Gmail | Google Agenda | Google Drive
Google Meet | Google Chat | Google Docs | Google Planilhas
Google Apresentações | Google Forms | Gemini | Segurança | Boas Práticas
```
Observe que os capítulos refletem como os usuários pensam e procuram informações, e que todos os assuntos relacionados a backup, por exemplo, permanecem agrupados, independentemente de serem procedimentos, incidentes ou conceitos.

## 3.7 Páginas e o Conceito de Artigo Atômico

A Página representa a menor unidade de conhecimento da Base. Cada Página deve responder a apenas uma necessidade — pode representar um procedimento, um incidente, um conceito, um tutorial, um FAQ ou um runbook. Entretanto, esses tipos não determinam a localização da página; eles serão representados por marcadores (conforme Capítulo 4).

**Princípio do Artigo Atômico:** Toda página deverá possuir um único objetivo, um único problema, uma única solução, uma única pergunta. Quanto menor for o escopo da página, maior será sua reutilização.

**Exemplos corretos:**

* *Como criar um backup utilizando pg_dump*
* *Como restaurar um backup utilizando pg_restore*
* *Erro: could not connect to server*
* *O que é WAL?*
* *Como compartilhar uma pasta no Google Drive*

**Exemplo incorreto:** *Manual Completo de Administração do PostgreSQL* — esse tipo de documento concentra diversos assuntos distintos e reduz significativamente a precisão da recuperação semântica.

## 3.8 Convenção de Nomenclatura

A nomenclatura deverá seguir padrões específicos conforme o nível da estrutura:

| Nível | Padrão | Exemplos |
|-------|--------|----------|
| **Estantes** | Escopo - Público-Alvo | `Embrapa - Suporte ao Usuário`, `Unidades - Operação de TI`, `Embrapa - Administração de TI` |
| **Livros** | Substantivos (nome oficial da tecnologia) | PostgreSQL, Docker, Google Workspace, VPN |
| **Capítulos** | Áreas funcionais | Backup e Recuperação, Segurança, Administração, Monitoramento |
| **Páginas** | Linguagem natural orientada à necessidade | *Como...*, *O que é...*, *Erro...*, *Não consigo...*, *Configurar...* |

Esses padrões favorecem tanto a pesquisa tradicional quanto a recuperação semântica.

## 3.9 Critérios para Criação de Novos Elementos

### Quando criar um novo Livro?

Antes da criação de um novo Livro, as seguintes perguntas deverão ser respondidas:

* Trata-se de um domínio de conhecimento permanente?
* Possui identidade própria?
* Gerará quantidade significativa de artigos?
* Não pode ser incorporado a outro Livro existente?

Caso qualquer resposta seja negativa, recomenda-se reavaliar a necessidade. Não é recomendável criar livros para projetos temporários, incidentes específicos, tecnologias pouco relevantes ou documentos isolados.

### Quando criar um novo Capítulo?

Um novo Capítulo deverá ser criado apenas quando existir um domínio funcional claramente distinto dentro do Livro. Por exemplo, no Livro Docker, "Volumes" justifica um capítulo próprio. Por outro lado, "Erro de Permissão" não justifica — trata-se de um tema para uma Página dentro do capítulo correspondente. Não devem existir capítulos baseados em formatos de documento, como "Procedimentos" ou "Incidentes", pois esses conceitos são representados pelo marcador `tipo`.

## 3.10 Navegação e Recuperação

A arquitetura foi concebida considerando dois mecanismos distintos de localização do conhecimento:

**Navegação hierárquica** — quando o usuário deseja explorar um assunto: Operação de TI → PostgreSQL → Backup e Recuperação → *Como restaurar backup*.

**Pesquisa** — quando o usuário realiza uma busca. Nesse caso, a localização hierárquica deixa de ser o principal fator, e o mecanismo de busca passa a utilizar conteúdo textual, marcadores, embeddings e contexto da pergunta. Essa combinação permite localizar artigos mesmo quando o usuário desconhece sua posição na estrutura do BookStack.

## 3.11 Exemplo Completo de Organização

Este exemplo ilustra o relacionamento lógico entre as estantes corporativas (`- Embrapa`) e locais (`- Unidades`):

```text
📚 Embrapa - Operação de TI (Central)
│
└── 📖 PostgreSQL
    ├── 📂 Instalação
    │   ├── Como instalar o PostgreSQL no Ubuntu
    │   └── Como atualizar para a versão 17
    ├── 📂 Backup e Recuperação
    │   ├── Como criar um backup utilizando pg_dump
    │   └── Como restaurar um backup utilizando pg_restore
    └── 📂 Segurança
        └── Configurar autenticação SCRAM

📚 Unidades - Operação de TI (Local)
│
└── 📖 TI - Embrapa Gado de Corte
    ├── 📂 Servidores Locais
    │   ├── Como executar backup local do banco de dados da Balança
    │   └── Configuração do AD Local (Read-Only Domain Controller)
    └── 📂 Infraestrutura de Rede Local
        └── Diagrama de Switches do Bloco de Laboratórios
```
Esse exemplo demonstra a aplicação dos princípios desta arquitetura: o analista local consulta os procedimentos centrais padrão de PostgreSQL na estante corporativa, mas documenta a sua rotina específica local e sua infraestrutura no livro dedicado de sua Unidade.
Esse exemplo ilustra a aplicação dos princípios apresentados neste documento: organização por domínio funcional, páginas atômicas, linguagem orientada à necessidade do usuário e separação entre estrutura e metadados.

## 3.12 Benefícios da Arquitetura da Informação

| Público | Benefícios |
|---------|-----------|
| **Usuários** | Navegação intuitiva, organização consistente, facilidade para localizar conteúdos relacionados |
| **Autores** | Estrutura padronizada, menor duplicação, facilidade de manutenção |
| **Governança** | Taxonomia uniforme, evolução controlada, redução de redundâncias |
| **Inteligência Artificial** | Maior coerência semântica, embeddings de melhor qualidade, melhor recuperação contextual, menor incidência de respostas irrelevantes |

---

# Capítulo 4 — Modelo Corporativo de Metadados e Taxonomia

## 4.1 Fundamentos: Estrutura versus Metadados

A arquitetura proposta distingue claramente dois conceitos fundamentais: a **Estrutura da Informação** (que organiza o conhecimento dentro da Base) e os **Metadados do Conhecimento** (que descrevem as características desse conhecimento). Essa separação reduz redundâncias, simplifica a manutenção e melhora significativamente a qualidade da recuperação semântica.

Todo marcador deve responder a uma pergunta que a estrutura da Base de Conhecimento não consegue responder. A estrutura informa *onde este artigo está*. Os marcadores informam *o que este artigo representa*.

**Não é recomendado criar marcadores que apenas repitam informações estruturais**, como `estante=equipe-ti-embrapa`, `livro=postgresql` ou `capitulo=backup`. Essa redundância aumenta o esforço de manutenção e cria risco de inconsistências. O pipeline de indexação poderá obter essas informações diretamente da API do BookStack.

## 4.2 Origem dos Metadados

Os metadados utilizados pelo mecanismo RAG possuem duas origens distintas:

### Metadados automáticos

Obtidos automaticamente da API do BookStack, sem qualquer preenchimento manual:

| Origem | Campo |
|--------|-------|
| Estrutura | Estante, Livro, Capítulo, Página |
| Sistema | ID da página, Autor, Data de criação, Data de atualização, URL, Permissões |

### Metadados editoriais

Definidos pelo autor do artigo. Representam características que a estrutura da Base não consegue expressar, como tipo do conhecimento, produto, versão, criticidade e classificação. Esses atributos enriquecem semanticamente o conteúdo e podem ser utilizados como filtros durante a recuperação no banco vetorial.

## 4.3 Marcadores Editoriais

### Marcador "Tipo" (obrigatório)

O marcador mais importante desta arquitetura identifica a natureza do conhecimento contido na página. É obrigatório para todas as páginas.

| Valor | Finalidade | Exemplo |
|-------|-----------|---------|
| `conceito` | Explica um assunto | *O que é WAL?* |
| `procedimento` | Ensina uma atividade | *Como criar um backup utilizando pg_dump* |
| `incidente` | Resolve um problema específico | *Erro "could not connect to server"* |
| `runbook` | Recuperação operacional ou resposta a eventos críticos | *Recuperação completa após corrupção do banco* |
| `tutorial` | Guia de aprendizado passo a passo | *Como instalar o Docker no Ubuntu* |
| `faq` | Responde perguntas frequentes | *Como altero minha senha?* |
| `referencia` | Reúne informações de consulta rápida | *Comandos úteis do Docker* |

### Marcador "Produto" (quando necessário)

O preenchimento desse marcador somente será necessário quando o produto não puder ser inferido pelo Livro ou quando o artigo envolver múltiplos produtos. Exemplo: uma página no Livro "Google Workspace" sobre integração com Microsoft Outlook utilizaria `produto=google-drive` e `produto=microsoft-outlook`.

### Marcador "Versão" (quando aplicável)

Utilizado quando o procedimento depende da versão da tecnologia (ex: `versao=17`, `versao=24.04`). Quando o conteúdo for independente da versão, o marcador poderá ser omitido.

### Marcador "Criticidade" (recomendado para operações)

Valores sugeridos: `baixa`, `média`, `alta`, `crítica`. Recomendado principalmente para Runbooks, procedimentos operacionais e recuperação de serviços.

### Marcador "Classificação" (opcional)

Identifica o nível de sensibilidade do conteúdo para fins de governança e auditoria. Valores sugeridos: `pública`, `interna`, `restrita`, `confidencial`. A utilização deverá seguir a política de segurança da informação da organização.

## 4.4 Marcadores que NÃO Devem Ser Utilizados

Para evitar redundâncias, os seguintes marcadores não deverão ser utilizados:

❌ `estante` · ❌ `livro` · ❌ `capítulo` · ❌ `página` · ❌ `autor` · ❌ `data` · ❌ `url`
❌ `unidade` (quando a unidade já estiver representada pelo Livro dentro das estantes dedicadas a Unidades, como "Unidades - Operação de TI" ou "Unidades - Suporte ao Usuário")

Essas informações são obtidas automaticamente pelo pipeline de indexação.

## 4.5 Exemplo Completo de Marcação

**Livro:** PostgreSQL · **Capítulo:** Backup e Recuperação · **Página:** *Como restaurar backup utilizando pg_restore*

**Marcadores:**
```text
tipo = procedimento
versao = 17
criticidade = alta
```
Observe que apenas três marcadores são suficientes para enriquecer semanticamente o artigo. Todo o restante será obtido automaticamente da estrutura da Base.

## 4.6 Taxonomia Corporativa

### O que é uma Taxonomia

Taxonomia é um modelo de classificação que responde à pergunta: *"Como a organização escolhe representar seus conhecimentos?"*. Na Base de Conhecimento, a taxonomia envolve nomenclatura, categorias, termos oficiais, relacionamentos, sinônimos, abreviações e metadados — representando um vocabulário controlado.

### Princípios da Taxonomia

**Princípio 1 — Um conceito, um nome oficial.** Cada conceito deve possuir apenas um nome oficial. O nome oficial deverá ser utilizado nos Livros, títulos, capítulos, artigos e marcadores. Exemplo: ✔ *Google Workspace* (nunca: GWS, Google Office, Workspace Google). ✔ *Active Directory* (nunca: AD, Microsoft AD, Diretório Ativo).

**Princípio 2 — Sinônimos são permitidos, mas controlados.** Embora exista apenas um nome oficial, usuários podem utilizar termos diferentes durante as pesquisas. O mecanismo de busca ou o pipeline de IA poderá manter um dicionário de sinônimos para expandir automaticamente a consulta, melhorando a recuperação sem alterar a documentação.

**Princípio 3 — Abreviações não substituem nomes oficiais.** As siglas podem aparecer no corpo do texto, porém não devem substituir o nome oficial nos títulos ou na estrutura. Exemplo: ✔ *Como configurar o Active Directory* (nunca: *Configuração do AD*).

### Vocabulário Controlado

A Governança deverá manter um catálogo de termos oficiais (detalhado no Anexo A):

| Conceito | Nome oficial | Sinônimos aceitos |
|----------|-------------|-------------------|
| Google Workspace | Google Workspace | GWS, Workspace |
| Active Directory | Active Directory | AD |
| Microsoft Entra ID | Microsoft Entra ID | Azure AD (legado) |
| PostgreSQL | PostgreSQL | Postgres |
| Docker Compose | Docker Compose | Compose |
| TOPdesk | TOPdesk | TopDesk (grafia incorreta) |

### Taxonomia dos Tipos de Conteúdo

A organização adota o conjunto padronizado de tipos definido na seção 4.3 (marcador "Tipo"). Esses valores deverão ser utilizados exclusivamente no marcador `tipo`.

### Taxonomia dos Domínios

Os Livros deverão representar domínios permanentes, organizados em grandes categorias:

| Categoria | Exemplos de Livros |
|-----------|-------------------|
| Infraestrutura | Linux, Windows Server, VMware, Docker, Kubernetes |
| Banco de Dados | PostgreSQL, MongoDB, SQL Server |
| Colaboração | Google Workspace, Microsoft 365, TOPdesk |
| Segurança | VPN, Firewall, Autenticação, MFA |

## 4.7 Relacionamentos e Ontologia do Conhecimento

A arquitetura incentiva a criação de relações explícitas entre páginas (ex: *Como criar backup PostgreSQL* → *Como validar backup PostgreSQL* → *Como restaurar backup PostgreSQL* → *Recuperação após desastre*). Esses relacionamentos criam uma rede de conhecimento que beneficia tanto a navegação quanto os sistemas RAG.

Como evolução do conceito de taxonomia, a arquitetura prevê uma camada de **ontologia** que responde não apenas a "como classificar o conhecimento", mas também a "como os conhecimentos se relacionam entre si":
```text
Google Workspace
    ├── contém → Google Drive, Gmail, Google Meet
    └── integra-se com → Microsoft Outlook

Docker
    ├── utiliza → Container, Volume, Rede
    └── pode armazenar → PostgreSQL

PostgreSQL
    ├── executa → Backup
    ├── utiliza → WAL
    └── integra-se com → Zabbix
```
Embora o BookStack não implemente uma ontologia de forma nativa, essa visão orienta a criação de links internos, referências cruzadas e futuras integrações com grafos de conhecimento (Knowledge Graphs).

## 4.8 Evolução e Governança dos Metadados

A taxonomia e os metadados deverão evoluir de forma controlada. Novos termos oficiais somente deverão ser adicionados quando representarem novos domínios de conhecimento, evitarem ambiguidades e possuírem aplicação permanente. Mudanças frequentes de nomenclatura devem ser evitadas, pois afetam links, referências, integrações e modelos de IA.

A inclusão de novos metadados deverá observar os critérios de necessidade recorrente, aplicação em diversos artigos, valor agregado à recuperação do conhecimento e não duplicação de informações já presentes na estrutura hierárquica. Novos metadados deverão ser aprovados pela Governança da Base de Conhecimento antes de sua adoção.

---

# Capítulo 5 — Metodologia KCS e Governança Editorial

## 5.1 Fundamentos do KCS

A metodologia **Knowledge-Centered Service (KCS)** tem como princípio fundamental transformar a resolução diária de demandas em uma oportunidade contínua de criação, evolução e reutilização do conhecimento. Nesta arquitetura, o KCS não é tratado como um processo independente, mas como um componente integrado à Base de Conhecimento.

O objetivo não é obrigar os colaboradores a produzir documentação extensa, mas garantir que o conhecimento de TI gerado durante a operação seja registrado de forma simples, reutilizável e continuamente aperfeiçoado. A Base de Conhecimento deixa de ser um repositório estático e passa a ser um sistema vivo, alimentado pelas atividades diárias das equipes.

## 5.2 Os Cinco Princípios do KCS

**Capturar enquanto se trabalha.** O conhecimento deve ser registrado durante ou imediatamente após a execução da atividade. Quanto maior o intervalo entre a execução e a documentação, maior a probabilidade de perda de informações relevantes.

**Reutilizar antes de criar.** Antes de produzir um novo artigo, o autor deverá verificar se já existe conteúdo semelhante. Sempre que possível, deve-se atualizar um artigo existente, complementar informações ou corrigir procedimentos. A criação de novos artigos deverá ocorrer apenas quando houver conhecimento realmente novo.

**Melhorar continuamente.** Nenhum artigo é considerado definitivo. Todo conteúdo poderá ser corrigido, ampliado, atualizado ou reorganizado. Essa evolução contínua é um dos pilares do KCS.

**Compartilhar o conhecimento.** Todo conhecimento produzido pertence à organização. A autoria é importante para fins de rastreabilidade, mas não representa propriedade sobre o conteúdo. Qualquer colaborador autorizado poderá contribuir para sua evolução.

**Aprender com o uso.** O uso da Base de Conhecimento gera informações valiosas. Perguntas recorrentes, buscas sem resultado e artigos pouco utilizados devem orientar melhorias contínuas.

## 5.3 Ciclo de Vida do Conhecimento

Todo artigo percorre um ciclo de vida contínuo:
```text
Necessidade → Criação → Publicação → Utilização → Revisão → Atualização → Nova Publicação
```
Esse ciclo nunca termina. Enquanto o conhecimento permanecer relevante, ele continuará evoluindo.

## 5.4 Papéis e Responsabilidades

A arquitetura define responsabilidades claras para quatro papéis:

| Papel | Responsabilidades |
|-------|-------------------|
| **Autor** | Registrar o conhecimento obtido durante a atividade. Não precisa produzir um documento perfeito — o principal objetivo é preservar o conhecimento. |
| **Revisor Técnico** | Verificar precisão técnica, consistência e atualização. Não altera a estrutura da Base. |
| **Gestor da Base de Conhecimento** | Organização, taxonomia, padrões editoriais, metadados e arquitetura. Não necessariamente revisa aspectos técnicos. |
| **Administrador do BookStack** | Infraestrutura, permissões, backups, integrações e disponibilidade. Não participa da produção dos artigos. |

## 5.5 Fluxo Editorial Integrado

A arquitetura recomenda o seguinte fluxo, integrando KCS com o processo de atendimento via TOPdesk:
```text
Atendimento/Incidente
    │
    ▼
Pesquisa na Base de Conhecimento
    │
    ├── Artigo encontrado → Utilizar → Atualizar se necessário → Resolver → Registrar reutilização
    │
    └── Artigo NÃO encontrado → Resolver incidente → Criar artigo → Revisão → Publicação → Indexação automática → Disponível para IA
```
Observe que a criação de conhecimento ocorre naturalmente durante a operação. A integração com o TOPdesk permite transformar atendimentos recorrentes em conhecimento reutilizável.

## 5.6 Qualidade e Reutilização do Conhecimento

### Reutilização como mecanismo de revisão

Sempre que um artigo for utilizado para resolver uma demanda, recomenda-se avaliar: permanece atualizado? Pode ser simplificado? Necessita novas imagens ou exemplos? Há novas versões da tecnologia? O uso cotidiano passa a ser um mecanismo permanente de revisão.

### Qualidade acima de Quantidade

A maturidade da Base não deve ser medida apenas pela quantidade de páginas. Uma Base com 2.000 artigos duplicados possui menor valor do que outra com 500 artigos bem estruturados. Indicadores de qualidade são mais relevantes do que indicadores de volume.

## 5.7 Indicadores de Maturidade KCS

A arquitetura recomenda acompanhar indicadores organizados em quatro dimensões:

| Dimensão | Indicadores |
|----------|-------------|
| **Produção** | Novos artigos publicados, artigos revisados, artigos atualizados |
| **Reutilização** | Quantidade de consultas, artigos utilizados em atendimentos, reutilização por equipe e por Unidade |
| **Qualidade** | Artigos duplicados, artigos obsoletos, artigos sem revisão, artigos sem utilização |
| **Evolução** | Tempo médio entre criação e publicação, tempo médio entre publicação e primeira reutilização, tempo médio entre revisões |

Esses indicadores podem ser consolidados em painéis de acompanhamento para apoiar a governança e orientar ações de melhoria contínua.

### Integração com Inteligência Artificial

A IA desempenha dois papéis no processo KCS:

* **Consumidora:** Consulta a Base para responder perguntas dos usuários via chatbots e agentes.
* **Colaboradora:** Auxilia na melhoria contínua, sugerindo títulos mais claros, identificando duplicidades, recomendando artigos relacionados, sugerindo marcadores, detectando conteúdo desatualizado e propondo reorganização de capítulos.

A IA auxilia o processo editorial, mas a aprovação permanece sob responsabilidade humana.

---

# Capítulo 6 — Governaça Corporativa e Descentralização

## 6.1 Princípio da Não Duplicação e Fonte Única da Verdade

A arquitetura adota o princípio de **Fonte Única da Verdade (Single Source of Truth)**. O BookStack será o repositório oficial do conhecimento corporativo. Todos os demais sistemas (Portal, Chatbot, banco vetorial/Qdrant) deverão consumir informações a partir dele.

Um mesmo conhecimento deverá existir apenas uma vez. Quando determinado conteúdo for necessário em diferentes contextos, deverá ser reutilizado por meio de referências ou links, evitando a criação de cópias.
```text
BookStack (Fonte Oficial)
         ┌──────┼──────┐
         ▼      ▼      ▼
      Portal  Chatbot  Banco Vetorial (Qdrant)
         └──────┼──────┘
                ▼
           Usuários
```
## 6.2 Critérios de Evolução Estrutural

A Base de Conhecimento deverá ser tratada como um sistema vivo. Os artigos não são considerados concluídos após sua publicação — devem evoluir continuamente, incorporando novas versões, mudanças de infraestrutura, novas soluções, lições aprendidas e sugestões dos usuários.

Os critérios para criação de novos elementos estruturais estão definidos no Capítulo 3 (seção 3.9). Qualquer criação de novos Livros, Capítulos ou alterações estruturais significativas deverá ser avaliada pela Governança da Base de Conhecimento.

## 6.3 Indicadores de Qualidade e Revisão Periódica

A governança deverá acompanhar indicadores de qualidade:

| Indicador | Objetivo |
|-----------|----------|
| Artigos publicados | Crescimento da Base |
| Artigos revisados | Atualização contínua |
| Artigos obsoletos | Necessidade de revisão |
| Artigos duplicados | Qualidade da taxonomia |
| Uso pelos usuários | Relevância da Base |
| Uso pelos analistas | Reutilização do conhecimento |
| Cobertura dos serviços | Maturidade da documentação |

### Revisão Periódica

Todo artigo deverá ser revisado periodicamente:

| Tipo de conteúdo | Periodicidade sugerida |
|-------------------|----------------------|
| Procedimentos operacionais | 12 meses |
| Runbooks | 6 meses |
| Artigos de conceitos | 24 meses |
| Conteúdo das Unidades | 12 meses |
| Artigos de segurança | Conforme política institucional ou após alterações relevantes |

Qualquer alteração significativa em um sistema ou serviço deverá desencadear a revisão dos artigos relacionados, independentemente do prazo definido.

### Estabilidade da Arquitetura

A arquitetura da Base de Conhecimento deverá permanecer estável ao longo do tempo. Mudanças estruturais (criação de novas Estantes, alterações na taxonomia, redefinição de padrões de metadados) deverão ser avaliadas por um processo formal de governança, evitando reorganizações frequentes que possam comprometer links, referências cruzadas, integrações e o processo de indexação para IA.

## 6.4 Conselho de Arquitetura do Conhecimento

Recomenda-se a criação de um **Conselho de Arquitetura do Conhecimento**, cujo papel não é revisar o conteúdo técnico dos artigos, mas sim preservar a coerência da arquitetura da informação. Suas responsabilidades incluem:

* definir e evoluir a taxonomia corporativa;
* aprovar a criação de novas Estantes e Livros;
* manter o modelo de metadados;
* acompanhar indicadores de qualidade da Base;
* orientar a evolução da integração com IA e sistemas RAG;
* garantir aderência aos princípios definidos neste documento.

Esse papel é semelhante ao de um Conselho de Arquitetura Corporativa em projetos de TI: em vez de decidir sobre cada documento, ele zela pela consistência do modelo como um todo.

## 6.5 Descentralização: Sede e Unidades

A Embrapa possui uma estrutura organizacional composta por uma Sede e diversas Unidades Descentralizadas distribuídas geograficamente. Embora grande parte dos serviços de TI seja padronizada, cada Unidade possui particularidades relacionadas à sua infraestrutura, processos, sistemas locais e forma de operação.

### Princípios da Descentralização

**Princípio 1 — O conhecimento é corporativo por padrão.** Todo novo artigo deve ser considerado inicialmente como potencialmente útil para toda a organização. Somente após essa avaliação deve-se decidir se ele será classificado como específico de uma Unidade.

**Princípio 2 — O conhecimento local é uma exceção.** Deve existir apenas quando representar uma diferença real (servidor exclusivo, sistema local, procedimento específico, equipamentos exclusivos, normas internas).

**Princípio 3 — Evoluir o artigo corporativo antes de criar um local.** A primeira ação deve ser contribuir para a evolução do artigo corporativo. A criação de um artigo local deve ocorrer apenas quando a informação não puder ser incorporada ao conteúdo corporativo.

**Princípio 4 — A arquitetura deve permanecer única.** Toda a documentação segue a mesma estrutura (Estantes, Livros, Capítulos, Páginas, Marcadores). Não existirão estruturas paralelas ou taxonomias específicas para determinadas Unidades.

**Princípio 5 — A IA deve compreender o contexto da Unidade.** Os sistemas de IA deverão distinguir quando uma pergunta exige uma resposta corporativa ou específica, utilizando metadados e contexto do usuário — não duplicação de documentos.

### A Regra 80/20

| Tipo de conhecimento | Percentual esperado |
|----------------------|:-------------------:|
| Conhecimento corporativo de TI (Embrapa) | 80% |
| Conhecimento específico de TI das Unidades Descentralizadas | 20% |

Caso uma Unidade possua uma proporção muito maior de conteúdo local, recomenda-se avaliar se parte desse conhecimento não poderia ser promovida à Base Corporativa.

## 6.6 Criação de Artigos Locais e Fluxo de Decisão

Antes de criar um artigo específico para uma Unidade, recomenda-se responder: (1) O conteúdo já existe na Base Corporativa? (2) A diferença é significativa? (3) A informação pode ser incorporada ao artigo corporativo? (4) O assunto interessa apenas à Unidade? (5) A manutenção separada é justificável?

### Organização das Estantes de Unidades

Em vez de centralizar todo o conteúdo das 44 unidades em uma única estante mista, o conhecimento descentralizado é distribuído de acordo com o público-alvo pelas três estantes dedicadas de Unidades:

```text
📚 Unidades - Suporte ao Usuário
├── 📖 Embrapa Cerrados - Suporte ao Usuário
│   ├── 📂 Ramais e Contatos Locais
│   ├── 📂 Impressão Local
│   └── 📂 Regras de Convivência e Acesso Local
└── 📖 Embrapa Gado de Corte - Suporte ao Usuário

📚 Unidades - Operação de TI
├── 📖 TI - Embrapa Cerrados
│   ├── 📂 Servidores Locais
│   ├── 📂 Infraestrutura de Rede Local
│   └── 📂 Telefonia e Links Locais
└── 📖 TI - Embrapa Gado de Corte

📚 Unidades - Administração de TI
├── 📖 Gestão TI - Embrapa Cerrados
│   ├── 📂 Inventário e Licenciamento Local
│   ├── 📂 Contratos Locais de TI
│   └── 📂 Plano de Continuidade Local
└── 📖 Gestão TI - Embrapa Gado de Corte
```

### Exemplo prático de coexistência

O procedimento geral corporativo *"Como configurar a impressora corporativa padrão"* é único e aplica-se a quase todas as localidades. No entanto, se na unidade *Embrapa Cerrados* houver uma impressora específica no Laboratório X com drivers especiais, o conteúdo é separado:

```text
📚 Embrapa - Suporte ao Usuário (Central)
└── 📖 Impressão → 📄 Como configurar a impressora corporativa padrão

📚 Unidades - Suporte ao Usuário (Local)
└── 📖 Embrapa Cerrados - Suporte ao Usuário → 📂 Impressão Local → 📄 Como configurar a impressora do Laboratório X
```

Dessa forma, o usuário da *Embrapa Cerrados* tem acesso a ambos os guias (central e local), sem haver duplicação do procedimento padrão corporativo.

### Fluxo de Decisão

```text
Novo conhecimento
       │
       ▼
Aplica-se a toda a organização?
       │
  ┌────┴────┐
 Sim       Não → É específico de uma Unidade?
  │              │
  ▼         ┌────┴────┐
Estantes   Sim       Não → Revisar classificação
Embrapa    │
           ▼
     Identificar o público-alvo (Usuário, TI ou Admin)
           │
           ▼
     Livro da Unidade correspondente na Estante de Unidade correspondente
```

## 6.7 Arquitetura de Camadas de Conhecimento

A Embrapa adota a **Arquitetura de Camadas de Conhecimento** como o modelo oficial para organizar, segmentar e recuperar informações com base no escopo organizacional e de abrangência de cada conteúdo. A base de conhecimento é dividida em três níveis concêntricos de relevância, integrados logicamente:

```text
┌─────────────────────────────────────────┐
│ Camada 1: Conhecimento Corporativo de TI  │ (Geral - 80% do acervo)
│  ┌───────────────────────────────────┐  │
│  │ Camada 2: Conhecimento Regional   │  │ (Compartilhado por grupo de UDs)
│  │  ┌─────────────────────────────┐  │  │
│  │  │ Camada 3: Conhecimento Local│  │  │ (Exclusivo da Unidade - 20%)
│  │  └─────────────────────────────┘  │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

### Detalhamento das Camadas

1. **Camada 1 — Conhecimento Corporativo:** Representa a fonte padrão de verdade para toda a instituição. Armazena conceitos, sistemas e procedimentos que possuem aplicação global nas estantes centrais: `Embrapa - Suporte ao Usuário`, `Embrapa - Operação de TI` e `Embrapa - Administração de TI`.
2. **Camada 2 — Conhecimento Regional/Coletivo:** Agrupa o conhecimento comum a um conjunto específico de Unidades Descentralizadas que compartilham o mesmo bioma, arranjo de pesquisa ou região geográfica. É implementado no BookStack por livros temáticos compartilhados ou qualificados via metadados específicos.
3. **Camada 3 — Conhecimento Local da Unidade:** Contém exclusivamente as particularidades técnicas, operacionais ou administrativas da Unidade Descentralizada. É armazenado na respectiva estante de Unidade (`Unidades - Suporte ao Usuário`, `Unidades - Operação de TI` ou `Unidades - Administração de TI`), dentro do livro da UD respectiva.

### Funcionamento e Integração com RAG

O pipeline de busca e o sistema de IA (RAG) consultam e recuperam as informações respeitando essa hierarquia. A prioridade de busca e a montagem de contexto obedecem às seguintes regras:

1. **Priorização Interna:** O sistema RAG consulta as camadas de forma cumulativa, mas prioriza o artigo mais específico ao usuário (Camada 3 > Camada 2 > Camada 1).
2. **Resolução de Conflitos:** Caso exista um procedimento geral corporativo e um local específico para a mesma tarefa, o sistema exibe e prioriza a particularidade local (Camada 3) para o usuário daquela respectiva Unidade, garantindo a aderência aos processos regionais sem duplicar a documentação corporativa básica.

---

# Capítulo 7 — Padrão Editorial e Redação de Artigos

## 7.1 Princípios de Redação

A qualidade da Base de Conhecimento depende diretamente da qualidade dos artigos produzidos. Uma arquitetura bem definida perde grande parte de seu valor quando os artigos são escritos de forma inconsistente, excessivamente longos ou misturam diferentes assuntos em uma única página.

Todos os artigos deverão utilizar linguagem objetiva, clara, impessoal, técnica e consistente.

**Evitar:**
* *"Talvez funcione..."* / *"Acho que..."* / *"Você pode tentar..."*

**Preferir:**
* *"Execute o comando abaixo."* / *"Verifique o resultado esperado."* / *"Caso o erro persista, prossiga para a próxima etapa."*

## 7.2 Estrutura Recomendada dos Artigos

Embora diferentes tipos de artigos possuam características próprias, recomenda-se que todos utilizem uma estrutura semelhante:

| Seção | Descrição |
|-------|-----------|
| **Título** | Deve refletir exatamente a necessidade do usuário. Evitar títulos genéricos. |
| **Contexto** | Apresenta rapidamente o cenário e o escopo. |
| **Sintoma ou Objetivo** | Procedimentos: objetivo da atividade. Incidentes: sintomas observados. Conceitos: definição resumida. |
| **Desenvolvimento** | Corpo principal do artigo, sempre dividido em etapas — nunca em grandes blocos de texto. |
| **Resultado esperado** | Como validar que o procedimento foi concluído com sucesso. |
| **Referências** | Links para artigos relacionados e documentação externa. |

## 7.3 Linguagem, Títulos, Imagens e Código

### Títulos orientados ao usuário

Os títulos devem refletir exatamente como o usuário pensa e pesquisa:

| Em vez de... | Utilizar... |
|-------------|-------------|
| *Autenticação* | *Como redefinir a senha do Google Workspace* |
| *VPN* | *Não consigo conectar na VPN* |
| *Docker* | *Como instalar o Docker no Ubuntu* |

### Capturas de tela

As imagens devem complementar o texto, nunca substituí-lo. Sempre que uma captura de tela for utilizada, o procedimento também deverá estar descrito em texto, garantindo acessibilidade, facilidade de atualização e melhor processamento pela IA.

### Código técnico

Todo comando deverá utilizar blocos de código com indicação da linguagem:
```bash
sudo systemctl restart docker
```
Nunca utilizar imagens contendo comandos.

### Links entre artigos

Os artigos devem formar uma rede de conhecimento. Sempre que existir conteúdo relacionado, utilizar links internos (ex: *"Veja também: Como criar backup utilizando pg_dump"*). Essa estratégia melhora a navegação humana e permite que futuros pipelines explorem relacionamentos entre artigos.

## 7.4 Critérios de Qualidade Editorial

Antes da publicação, todo artigo deve responder positivamente às seguintes perguntas:

* Resolve apenas um problema?
* Está atualizado?
* Possui título objetivo?
* Utiliza linguagem clara?
* Contém apenas um assunto principal?
* Está no Livro e Capítulo corretos?
* Possui o marcador `tipo`?
* Há artigos semelhantes que deveriam ser consolidados?

Se qualquer resposta for negativa, recomenda-se revisar o artigo antes da publicação.

## 7.5 Reutilização e Independência

O principal objetivo de um artigo não é documentar um evento específico, mas permitir que qualquer colaborador consiga reproduzir a solução sem depender do autor original. Um bom artigo deve ser compreensível, reutilizável, independente, atualizado e verificável — atributos que representam os pilares da gestão do conhecimento baseada em KCS.

---

# Capítulo 8 — Templates Corporativos de Artigos

## 8.1 Objetivo e Convenções Gerais

Este capítulo estabelece modelos padronizados para elaboração dos artigos da Base de Conhecimento. A utilização de templates padroniza a documentação, reduz o tempo de produção, facilita a leitura, aumenta a reutilização, melhora a recuperação por mecanismos RAG e garante consistência editorial.

**Convenções para todos os templates:**

* utilizar títulos claros e objetivos;
* escrever em linguagem impessoal;
* evitar parágrafos excessivamente longos;
* utilizar listas numeradas em procedimentos;
* incluir exemplos sempre que possível;
* utilizar imagens apenas quando agregarem valor;
* referenciar artigos relacionados;
* revisar periodicamente o conteúdo.

Novos templates deverão ser criados apenas quando representarem um padrão recorrente de documentação.

## 8.2 Template — Conceito
```text
Título:       [O que é <conceito>?]
Objetivo:     [Apresentar o conceito ao leitor]
Definição:    [Descrição técnica do conceito]
Como funciona:[Explicação do funcionamento]
Quando usar:  [Cenários de aplicação]
Vantagens:    [Benefícios]
Limitações:   [Restrições ou cuidados]
Veja também:  [Artigos relacionados]
Referências:  [Documentação externa]
```
**Exemplo:** *"O que é PostgreSQL?"* — apresenta visão geral, funcionamento, cenários de uso, vantagens, limitações e links para artigos sobre Backup, Replicação e Monitoramento.

## 8.3 Template — Procedimento
```text
Título:            [Como <ação> utilizando <ferramenta>]
Objetivo:          [Finalidade do procedimento]
Pré-requisitos:    [O que é necessário antes de iniciar]
Procedimento:      [Passo 1, Passo 2, Passo 3...]
Validação:         [Como verificar o resultado]
Resultado esperado:[O que deve acontecer ao final]
Problemas comuns:  [Erros frequentes e soluções]
Referências:       [Documentação externa]
```
## 8.4 Template — Incidente
```text
Título:            [Erro "<mensagem de erro>"]
Sintoma:           [O que o usuário observa]
Causa provável:    [Razão técnica do problema]
Diagnóstico:       [Como confirmar a causa]
Solução:           [Passos para resolver]
Validação:         [Como confirmar a correção]
Prevenção:         [Como evitar recorrência]
Referências:       [Links relacionados]
```
## 8.5 Template — Runbook
```text
Título:               [Runbook — <operação crítica>]
Objetivo:             [Finalidade da operação]
Quando executar:      [Condições de disparo]
Responsáveis:         [Equipe ou função responsável]
Pré-requisitos:       [Acessos, ferramentas, permissões]
Passo a passo:        [Procedimento detalhado]
Pontos de verificação:[Checkpoints durante a execução]
Critério de sucesso:  [Como confirmar conclusão]
Plano de reversão:    [Procedimento de rollback]
Contatos:             [Escalonamento]
Referências:          [Links relacionados]
```
## 8.6 Template — FAQ
```text
Título:                [Pergunta frequente em linguagem natural]
Resposta:              [Resposta objetiva]
Informações adicionais:[Detalhes complementares]
Veja também:           [Links relacionados]
```
## 8.7 Template — Tutorial
```text
Título:              [Como <aprender/fazer> <assunto>]
Objetivo:            [O que o leitor aprenderá]
Público:             [Nível de conhecimento esperado]
Conhecimentos prévios:[O que o leitor já deve saber]
Passo 1...N:         [Sequência de aprendizado]
Exercício:           [Prática sugerida]
Próximos passos:     [Continuação do aprendizado]
```
## 8.8 Template — Referência
```text
Título:       [<Assunto> — Referência Rápida]
Descrição:    [Contexto de uso]
Tabela/Lista: [Comandos, parâmetros ou configurações]
Observações:  [Notas importantes]
Referências:  [Documentação oficial]
```
## 8.9 Outros Templates

### Template — Arquitetura
```text
Objetivo | Escopo | Arquitetura (diagrama) | Componentes | Fluxo
Integrações | Dependências | Limitações | Diagramas | Referências
```
### Template — Serviço
```text
Nome do Serviço | Descrição | Público | Responsável | Criticidade
Requisitos | Solicitação | Fluxo | SLA | Relacionamentos
```
### Template — Sistema
```text
Descrição | Objetivo | Arquitetura | Módulos | Integrações
Requisitos | Usuários | Permissões | Backup | Monitoramento | Referências
```
### Template — Boas Práticas
```text
Objetivo | Recomendações | O que evitar | Checklist | Referências
```
## 8.10 Templates Inteligentes

Como evolução dos modelos estáticos, a organização pode adotar um **Assistente de Criação de Artigos**:
```text
Autor → Escolhe o tipo do artigo → IA identifica o template →
Modelo preenchido automaticamente → Autor revisa → Publica
```
Nesse cenário, o autor não precisa conhecer todos os templates. Basta informar que deseja criar um "Procedimento", um "Runbook" ou um "Incidente", e o sistema apresenta automaticamente a estrutura adequada. No futuro, esse assistente poderá sugerir títulos, metadados, artigos relacionados e identificar possíveis duplicidades antes da publicação.

---

# Capítulo 9 — Arquitetura Técnica de Recuperação e IA (RAG)

## 9.1 Visão Geral do Pipeline de Indexação

A Base de Conhecimento não será utilizada exclusivamente por pessoas — ela também será consumida por mecanismos de Inteligência Artificial, motores de busca semântica, sistemas RAG e agentes inteligentes. Por esse motivo, o conteúdo deverá percorrer um processo de transformação antes de ser armazenado no banco vetorial (Qdrant).

Esse processo, denominado **Pipeline de Indexação**, transforma artigos escritos para seres humanos em documentos estruturados e semanticamente enriquecidos para consumo por modelos de linguagem:
```text
BookStack → n8n (Orquestração) → API do BookStack → Extração do Conteúdo →
Enriquecimento dos Metadados → Chunking Inteligente → Geração dos Embeddings →
Banco Vetorial (Qdrant) → Sistema RAG / IA
```
O **n8n** atua como camada de orquestração, sendo responsável pelo acesso à API do BookStack, pela automação dos fluxos de extração e pelo encaminhamento dos dados processados ao banco vetorial (Qdrant).

Cada etapa possui responsabilidades próprias e independentes. Essa separação facilita a evolução do sistema sem necessidade de alterar a Base de Conhecimento.

### Arquitetura em Quatro Domínios
```text
PRODUÇÃO                    ORGANIZAÇÃO DO CONHECIMENTO
(Autores, Especialistas)    (BookStack, Taxonomia, Metadados, Templates, Governança)
        │                           │
        ▼                           ▼
RECUPERAÇÃO DO CONHECIMENTO APLICAÇÃO DO CONHECIMENTO
(n8n, Pipeline, Chunking,   (TOPdesk, Portal, Chatbot,
 Embeddings, Banco Vetorial,  Agentes IA, APIs, Dashboards)
 Busca Híbrida, Re-ranking)
```
### Arquitetura Lógica em Oito Camadas

| Camada | Responsabilidade |
|--------|-----------------|
| 1. Produção | Autores criam e revisam artigos |
| 2. BookStack | Armazenamento, organização e versionamento |
| 3. Pipeline | Extração, normalização, chunking e enriquecimento |
| 4. Banco Vetorial (Qdrant) | Armazenamento de vetores e metadados |
| 5. Recuperação | Busca híbrida, filtros e re-ranking |
| 6. LLM | Compreensão, interpretação e síntese de respostas |
| 7. Aplicações | Chatbots, APIs e agentes inteligentes |
| 8. Governança | Indicadores, revisão e evolução contínua |

## 9.2 Extração, Enriquecimento e Chunking Inteligente

### Etapa 1 — Extração

A primeira etapa, orquestrada pelo n8n, obtém as páginas do BookStack via API, recuperando: título, conteúdo em Markdown/HTML, marcadores, autor, datas, permissões e localização na estrutura (Estante, Livro, Capítulo). Todo o processo ocorre automaticamente — os autores não precisam realizar qualquer ação adicional.

### Etapa 2 — Enriquecimento

O pipeline complementa o documento com metadados adicionais obtidos da estrutura:
```json
{
    "estante": "Embrapa - Operação de TI",
    "livro": "PostgreSQL",
    "capitulo": "Backup e Recuperação",
    "tipo": "procedimento",
    "versao": "17"
}
```
Esses metadados serão armazenados juntamente com os embeddings e permitirão filtros rápidos durante a recuperação.

### Etapa 3 — Chunking Inteligente

Um dos erros mais comuns em projetos RAG consiste em dividir documentos utilizando apenas quantidade de caracteres. Embora simples, essa abordagem frequentemente separa informações que deveriam permanecer juntas. Nesta arquitetura, o chunking será orientado pela **estrutura lógica do artigo** (Título, Sintoma, Contexto, Causa, Resolução, Referências).

**Exemplo de chunking estrutural:**
```text
Chunk 1: Título + Sintoma + Contexto
Chunk 2: Causa + Resolução
Chunk 3: Referências + Observações
```
Cada bloco mantém um contexto completo, melhorando significativamente a qualidade dos embeddings.

## 9.3 Embeddings e Payload do Banco Vetorial (Qdrant)

Após a divisão, cada chunk será convertido em um vetor numérico que representa seu significado semântico. O banco vetorial (Qdrant) armazenará vetor, texto original, metadados e identificadores.

**Estrutura sugerida para o Payload:**
```json
{
  "id": 834,
  "texto": "...",
  "embedding": [...],
  "metadata": {
    "estante": "Embrapa - Operação de TI",
    "livro": "PostgreSQL",
    "capitulo": "Backup e Recuperação",
    "pagina": "Como restaurar backup utilizando pg_restore",
    "tipo": "procedimento",
    "versao": "17",
    "criticidade": "alta",
    "escopo": "corporativo",
    "unidade": null
  }
}
```
Essa estrutura permite utilizar filtros antes mesmo da busca vetorial. Para artigos de Unidades específicas, o campo `escopo` recebe o valor `"unidade"` e o campo `unidade` identifica a Unidade correspondente.

## 9.4 Modelos de Busca

A arquitetura prevê quatro mecanismos complementares de busca:

| Tipo | Quando utilizar | Exemplo |
|------|----------------|---------|
| **Navegação estruturada** | Usuário sabe onde procurar | Equipe TI → Docker → Volumes → *Como criar um volume* |
| **Busca lexical** | Existe uma palavra conhecida | `pg_restore` |
| **Busca semântica vetorial** | Existe apenas uma intenção | *"Meu banco caiu depois da troca do servidor"* |
| **Busca contextualizada** | IA considera perfil, Unidade, permissões e histórico | Duas pessoas recebem respostas diferentes para a mesma pergunta |

**Decisão arquitetural importante:** O BookStack é o sistema oficial de **autoria** (criação, organização, revisão, publicação, versionamento). A recuperação inteligente do conhecimento será responsabilidade de outra camada da arquitetura.

## 9.5 Pipeline de Recuperação: Expansão, Re-ranking e Montagem de Contexto

O pipeline de recuperação segue o fluxo:
```text
Pergunta → Normalização → Expansão Semântica → Busca Lexical + Busca Vetorial →
Filtros → Re-ranking → Montagem do Contexto → LLM → Resposta
```
O LLM aparece somente no final — propositalmente. O modelo de linguagem nunca deve ser a primeira etapa.

### Expansão Semântica

Antes da pesquisa, o sistema enriquece automaticamente a pergunta. Exemplo: *"Não consigo abrir meu Drive"* pode ser expandido para: Google Drive, Workspace, Compartilhamento, Permissões, Erro de acesso.

### Busca Híbrida

A recuperação combina busca lexical (localiza palavras exatas) e busca vetorial (localiza significado). Nenhuma deve substituir completamente a outra — cada mecanismo resolve problemas diferentes.

### Re-ranking

Após recuperar os documentos, eles são reclassificados por: similaridade semântica, proximidade lexical, atualização, reutilização, qualidade editorial, escopo organizacional e permissões.

### Montagem do Contexto

O modelo de linguagem recebe não apenas o texto encontrado, mas também: a pergunta original, os trechos recuperados, os metadados associados, os relacionamentos entre artigos e o contexto organizacional (Unidade, perfil do usuário). Essa combinação reduz alucinações e melhora a precisão.

## 9.6 Papel dos Componentes

| Componente | Responsabilidade | NÃO é responsável por |
|------------|-----------------|----------------------|
| **BookStack** | Autoria, organização, revisão, publicação, versionamento | Busca inteligente, RAG |
| **n8n** | Orquestração do pipeline, acesso à API do BookStack, automação dos fluxos de indexação | Autoria, armazenamento de conteúdo, busca |
| **Banco Vetorial (Qdrant)** | Armazenar vetores e metadados, busca por similaridade | Autoria, governança, workflow |
| **LLM** | Compreender perguntas, interpretar contexto, sintetizar respostas | Criar conhecimento, decidir políticas, substituir a Base |

Toda informação apresentada pelo LLM deverá ser baseada na Base Corporativa.

## 9.7 Integrações

### Integração com o TOPdesk
```text
Chamado → TOPdesk → Pesquisa automática → BookStack → Artigo encontrado?
├── Sim → Resolver incidente → Registrar reutilização → Indicadores KCS
└── Não → Atendimento → Novo conhecimento → BookStack → n8n → Pipeline → Banco Vetorial (Qdrant)
```
### Integração com ITAM e CMDB

A arquitetura prevê integração com a Gestão de Ativos e Configuração, permitindo que artigos estejam relacionados a serviços, ativos, sistemas, fornecedores e tecnologias.

## 9.8 Camadas da Arquitetura e Independência Tecnológica

A arquitetura foi construída para ser independente de fornecedores. Todos os componentes — BookStack, n8n, banco vetorial (Qdrant), modelos de linguagem (OpenAI, Gemini, Claude, Llama, DeepSeek), frameworks (LangChain, LlamaIndex, Haystack) — poderão ser substituídos sem necessidade de alterar a taxonomia, os artigos, os templates, a governança ou os processos KCS.

Essa é uma das principais características de arquiteturas corporativas maduras: **o conhecimento é o ativo permanente da organização**, não as ferramentas tecnológicas.

### Evolução para "Knowledge as Code"

A Base de Conhecimento pode ser tratada como um sistema vivo, semelhante ao conceito de *Infrastructure as Code*. Cada alteração em uma página gera automaticamente uma nova indexação, novos embeddings e atualização do banco vetorial. O conhecimento deixa de ser um documento estático e passa a ser um ativo continuamente processado e distribuído.

## 9.9 Visão Arquitetural Integrada
```text
PESSOAS
                       │
     ┌─────────────────┼─────────────────┐
 Especialistas     Analistas        Usuários
     └─────────────────┼─────────────────┘
                       │
                PRODUÇÃO DO CONHECIMENTO (Metodologia KCS)
                       │
                       ▼
             BOOKSTACK (Fonte Oficial)
                       │
        ┌──────────────┼──────────────┐
   Taxonomia      Templates      Metadados
        └──────────────┼──────────────┘
                       │
            n8n (Orquestração)
                       │
                 Pipeline RAG
                       │
      Extração → Chunking → Embeddings
                       │
            Banco Vetorial (Qdrant)
                       │
         Busca Híbrida + Re-ranking
                       │
                      LLM
                       │
        ┌──────────────┼──────────────┐
     Chatbot      TOPdesk      Agentes IA
        └──────────────┼──────────────┘
                       │
              FEEDBACK E MELHORIA CONTÍNUA (KCS)
```
### Os Cinco Ativos Estratégicos

Toda a arquitetura pode ser sintetizada em cinco ativos corporativos interdependentes:

| Ativo | Representação |
|-------|--------------|
| **Conhecimento** | Artigos da Base |
| **Estrutura** | BookStack e hierarquia organizacional |
| **Semântica** | Taxonomia, metadados e ontologia |
| **Inteligência** | Pipeline RAG, n8n, banco vetorial (Qdrant) e LLM |
| **Governança** | Metodologia KCS e Conselho de Arquitetura |

---

# Capítulo 10 — Roadmap de Implementação e Modelo de Maturidade

## 10.1 Estratégia de Implantação

A implantação deverá ocorrer de forma gradual, minimizando impactos na operação e permitindo o amadurecimento contínuo dos processos, da governança e da tecnologia. A estratégia organiza a implementação em oito fases evolutivas, nas quais cada etapa gera benefícios concretos e prepara a organização para a etapa seguinte.

## 10.2 Fases do Projeto
```text
FASE 1: Infraestrutura → FASE 2: Arquitetura da Informação → FASE 3: Produção do Conhecimento →
FASE 4: Governança → FASE 5: Integração → FASE 6: Inteligência Artificial →
FASE 7: Agentes Inteligentes → FASE 8: Melhoria Contínua
```
### FASE 1 — Infraestrutura

**Objetivo:** Disponibilizar o ambiente tecnológico.

**Entregas:** Implantação do BookStack, configuração de autenticação (LDAP/SSO), backup, HTTPS, controle de permissões, ambiente de homologação e monitoramento.

**Critério de conclusão:** A plataforma encontra-se operacional e disponível para uso.

### FASE 2 — Arquitetura da Informação

**Entregas:** Criação das Estantes e Livros, definição dos Capítulos, padronização dos marcadores, definição da taxonomia, convenções de nomenclatura e modelo de metadados.

**Critério de conclusão:** Toda nova documentação já segue o modelo arquitetural.

### FASE 3 — Produção do Conhecimento

**Atividades:** Capacitação dos autores, padronização dos artigos, migração da documentação existente, criação dos primeiros procedimentos e runbooks, definição do fluxo editorial.

**Critério de conclusão:** A Base passa a ser utilizada diariamente.

### FASE 4 — Governança

**Entregas:** Conselho de Arquitetura do Conhecimento, revisões periódicas, indicadores, processo editorial, responsáveis por domínio e política de atualização.

**Critério de conclusão:** O conhecimento passa a evoluir continuamente.

### FASE 5 — Integração

**Integrações previstas:** TOPdesk, Active Directory, Google Workspace, Zabbix, OCS Inventory e APIs corporativas.

**Fluxos:** Abertura de chamados, consulta automática, criação de artigos, atualização de ativos e notificações.

### FASE 6 — Inteligência Artificial

**Componentes:** BookStack → n8n → Pipeline → Embeddings → Banco Vetorial (Qdrant) → RAG → LLM.

**Entregas:** Pipeline automatizado, vetorização, busca híbrida, re-ranking e chatbot corporativo.

### FASE 7 — Agentes Inteligentes

A IA deixa de apenas responder perguntas e passa a colaborar com os processos: diagnóstico assistido, geração automática de runbooks, recomendação de procedimentos, classificação de chamados, sugestão de artigos, identificação de duplicidades e revisão textual.

### FASE 8 — Melhoria Contínua

A arquitetura entra em operação permanente. Objetivos: acompanhar indicadores, revisar taxonomia, medir reutilização, acompanhar evolução da IA, incorporar novas tecnologias e aperfeiçoar continuamente a Base. A melhoria contínua deixa de ser um projeto e passa a fazer parte da rotina da organização.

## 10.3 Indicadores de Progresso por Fase

| Fase | Indicadores sugeridos |
|------|----------------------|
| Infraestrutura | Disponibilidade, backups, autenticação |
| Arquitetura | Percentual de conteúdo estruturado conforme o modelo |
| Produção | Novos artigos, migração concluída |
| Governança | Revisões realizadas, duplicidades identificadas |
| Integração | Sistemas integrados, consultas automáticas |
| IA | Precisão das respostas, cobertura do RAG |
| Agentes | Processos automatizados, sugestões aceitas |
| Melhoria Contínua | Evolução dos indicadores ao longo do tempo |

## 10.4 Fatores Críticos de Sucesso

A implantação dependerá principalmente de fatores organizacionais:

* apoio da alta gestão;
* participação ativa das equipes;
* compromisso com a governança;
* atualização constante do conteúdo;
* integração entre áreas;
* cultura de compartilhamento do conhecimento.

A tecnologia, por si só, não garante o sucesso da iniciativa.

## 10.5 Análise de Riscos e Mitigações

| Risco | Descrição | Mitigação |
|-------|-----------|-----------|
| **Produção insuficiente** | Poucos artigos publicados | Integrar criação de artigos ao fluxo operacional (KCS); gamificação |
| **Duplicidade** | Várias versões do mesmo procedimento | Governança ativa; pesquisa obrigatória antes da criação |
| **Obsolescência** | Conteúdo desatualizado | Revisão periódica; marcadores de data de revisão |
| **Baixa reutilização** | A Base existe, mas ninguém consulta | Integração com TOPdesk; chatbot; treinamento |
| **Dependência de pessoas** | Conhecimento permanece apenas com especialistas | Captura contínua (KCS); incentivo à documentação |
| **IA sem governança** | Modelos respondem utilizando fontes não controladas | Toda resposta de IA fundamentada na Base oficial |

## 10.6 Modelo de Maturidade da Gestão do Conhecimento

| Nível | Denominação | Características |
|:-----:|-------------|----------------|
| 1 | **Documentação** | Informações dispersas, pouca padronização e baixa reutilização |
| 2 | **Organização** | Base estruturada, taxonomia definida e padrão editorial estabelecido |
| 3 | **Governança** | Processos de revisão, indicadores e papéis bem definidos |
| 4 | **Inteligência** | Conteúdo indexado para RAG, busca híbrida e apoio de IA generativa |
| 5 | **Conhecimento Inteligente** | Agentes de IA, automações, conhecimento contextualizado e melhoria contínua baseada em métricas |

Esse modelo pode ser utilizado para avaliar periodicamente a evolução da iniciativa e orientar o planejamento das próximas ações.

---

# Considerações Finais

Este documento estabelece as bases para a transformação da gestão do conhecimento de TI da Embrapa. A arquitetura proposta vai além da implantação de uma plataforma tecnológica — ela define um modelo corporativo de produção, organização, recuperação e evolução contínua do conhecimento de TI.

Os doze princípios fundamentais orientam todas as decisões de arquitetura. A separação entre estrutura e classificação garante escalabilidade. A metodologia KCS transforma a operação diária em fonte permanente de conhecimento de TI. A arquitetura RAG e os bancos vetoriais (Qdrant) ampliam a capacidade de recuperação para além das limitações da busca textual tradicional.

O sucesso dessa iniciativa dependerá menos da tecnologia empregada e mais do compromisso institucional com a governança, a colaboração e a melhoria contínua. A Base de Conhecimento não é um projeto com data de término — é uma capacidade organizacional que deverá evoluir permanentemente, acompanhando as mudanças tecnológicas, os novos desafios operacionais e as oportunidades oferecidas pela Inteligência Artificial.

A Embrapa, ao adotar esta arquitetura, posiciona-se para construir uma Base de Conhecimento que seja simultaneamente útil para pessoas, eficiente para mecanismos de busca, semanticamente rica para sistemas de IA e resiliente diante das inevitáveis mudanças tecnológicas dos próximos anos.

---

# Anexo A — Dicionário Corporativo e Vocabulário Controlado

## A.1 Objetivo

Este anexo estabelece o vocabulário oficial utilizado na Base de Conhecimento Corporativa. Seu objetivo é garantir que todos os autores utilizem a mesma terminologia para representar os mesmos conceitos. Essa padronização reduz ambiguidades, melhora a pesquisa textual, aumenta a qualidade dos embeddings e favorece a recuperação semântica.

## A.2 Modelo de Registro

Todo conceito deverá possuir: nome oficial, definição, sinônimos conhecidos, siglas, termos relacionados e observações. Apenas o **nome oficial** deverá ser utilizado na estrutura da Base.

| Campo | Descrição |
|-------|-----------|
| Nome Oficial | Nome utilizado na Base |
| Categoria | Tecnologia, Serviço, Processo, Sistema etc. |
| Definição | Descrição resumida |
| Sinônimos | Termos utilizados pelos usuários |
| Siglas | Abreviações conhecidas |
| Relacionamentos | Outros conceitos relacionados |
| Observações | Informações adicionais |

## A.3 Exemplos de Registro

### Google Workspace

| Campo | Valor |
|-------|-------|
| Nome Oficial | Google Workspace |
| Categoria | Plataforma de Colaboração |
| Definição | Conjunto de serviços de colaboração em nuvem do Google |
| Sinônimos | Workspace |
| Siglas | GWS |
| Relacionamentos | Gmail, Google Drive, Google Meet, Google Agenda |
| Observações | Sempre utilizar "Google Workspace" como nome oficial |

### PostgreSQL

| Campo | Valor |
|-------|-------|
| Nome Oficial | PostgreSQL |
| Categoria | Banco de Dados |
| Definição | Sistema Gerenciador de Banco de Dados Relacional |
| Sinônimos | Postgres |
| Relacionamentos | pg_dump, pg_restore, WAL, Replicação |
| Observações | Utilizar "PostgreSQL" em títulos e metadados |

### Active Directory

| Campo | Valor |
|-------|-------|
| Nome Oficial | Active Directory |
| Categoria | Serviço de Diretório |
| Sinônimos | AD |
| Relacionamentos | LDAP, Kerberos, DNS |
| Observações | Evitar utilizar apenas "AD" em títulos |

## A.4 Categorias Oficiais

Todo conceito deverá pertencer a uma categoria: Tecnologia, Serviço, Sistema, Processo, Equipamento, Infraestrutura, Banco de Dados, Rede, Segurança, Aplicação, Normativo, Ferramenta, Integração.

## A.5 Regras para Novos Conceitos

Antes de criar um novo termo oficial, verificar: já existe um conceito equivalente? Existe outra grafia oficial? Trata-se apenas de um sinônimo? O conceito é permanente? Será utilizado por mais de uma equipe? Somente após essa análise o conceito deverá ser incorporado ao dicionário.

## A.6 Grafia Oficial

A Base deverá manter uma única grafia. Exemplos:

| Correto | Incorreto |
|---------|-----------|
| TOPdesk | TopDesk, TOPDesk, TOP DESK |
| BookStack | Book Stack, Bookstack |
| Google Workspace | Workspace Google, Google Office |

## A.7 Termos Obsoletos

Quando um conceito deixar de ser utilizado, ele não deverá ser removido imediatamente. O dicionário deverá indicar: situação (Obsoleto), substituído por (novo conceito), data da alteração. Exemplo: *Azure Active Directory* → substituído por *Microsoft Entra ID*.

## A.8 Relações Semânticas e Governança

Cada conceito poderá possuir relacionamentos explícitos que poderão ser utilizados futuramente para construção de grafos de conhecimento. O Dicionário Corporativo deverá possuir um responsável, cujas atribuições incluem: aprovar novos conceitos, eliminar duplicidades, revisar grafias, manter sinônimos e acompanhar mudanças tecnológicas.

Como evolução, a organização pode migrar de um vocabulário de termos para um **Catálogo Corporativo de Conhecimento**, no qual cada conceito passa a ser tratado como um ativo com proprietário, sistemas, serviços, processos, artigos e indicadores relacionados.

---

# Anexo B — Referência de Metadados e Payload

## B.1 Objetivo

Este anexo define o modelo oficial detalhado de metadados utilizado na Base de Conhecimento Corporativa, complementando as diretrizes do Capítulo 4.

## B.2 Classificação dos Metadados

### Metadados Obrigatórios

| Campo | Descrição | Valores |
|-------|-----------|---------|
| `tipo` | Natureza do artigo | `conceito`, `procedimento`, `tutorial`, `incidente`, `runbook`, `faq`, `referencia` |
| `serviço` | Serviço de TI relacionado | Google Workspace, Docker, VPN, PostgreSQL, TOPdesk, Backup... |
| `público` | Público-alvo | `usuario-final`, `equipe-ti`, `administrador`, `gestor` |
| `criticidade` | Importância operacional | `baixa`, `media`, `alta`, `critica` |

### Metadados Recomendados

| Campo | Descrição | Exemplos |
|-------|-----------|----------|
| `plataforma` | Tecnologia específica | Windows, Linux, Android, iOS, Web, Docker |
| `versão` | Versão documentada | Ubuntu 24.04, PostgreSQL 17, Docker 28 |
| `autor-responsavel` | Equipe responsável (não pessoa) | Infraestrutura, Banco de Dados, Service Desk, Segurança |
| `revisao` | Data prevista para revisão | 2027-01 |
| `palavras-chave` | Termos relevantes | postgresql, backup, pg_dump, restore, wal |

### Metadados Específicos

| Campo | Quando utilizar | Exemplos |
|-------|----------------|----------|
| `unidade` | Artigo de Unidade específica | Embrapa Cerrados |
| `sistema` | Artigo sobre sistema corporativo | SIGA, SEI, TOPdesk |
| `ativo` | Relacionado a ativo de TI | Servidor PostgreSQL, Firewall Fortigate |
| `fornecedor` | Quando relevante | Google, Microsoft, Oracle, Red Hat |
| `integração` | Outros sistemas envolvidos | TOPdesk, Zabbix, LDAP, Vaultwarden |

## B.3 Metadados NÃO Utilizados

Para manter a simplicidade, alguns campos foram deliberadamente excluídos:

| Campo | Motivo |
|-------|--------|
| `indexação` | Todo artigo publicado é automaticamente indexado pelo pipeline |
| `embedding` | Responsabilidade exclusiva do pipeline de IA |
| `chunk` | Fragmentação ocorre automaticamente durante a indexação |
| `vetor` | Armazenamento pertence ao banco vetorial (Qdrant) |
| `modelo-ia` | Arquitetura independente do modelo utilizado |
| `score` | Pontuações de similaridade pertencem ao mecanismo de recuperação |

Essas informações pertencem à infraestrutura tecnológica, não aos autores dos artigos.

## B.4 Exemplos Práticos de Payload

### Artigo corporativo
```yaml
tipo: procedimento
serviço: PostgreSQL
público: equipe-ti
criticidade: alta
plataforma: Linux
versão: PostgreSQL 17
autor-responsavel: Banco de Dados
revisao: 2027-01
palavras-chave:
  - backup
  - pg_dump
  - restore
```
### Artigo de Unidade
```yaml
tipo: procedimento
serviço: Impressão
público: usuario-final
criticidade: media
unidade: Embrapa Cerrados
plataforma: Windows
autor-responsavel: Suporte Local
```

## B.5 Convenção de Escrita

Todos os valores deverão seguir as seguintes regras:

* utilizar singular;
* evitar abreviações desnecessárias;
* respeitar a nomenclatura oficial definida na Taxonomia Corporativa (Anexo A);
* utilizar sempre a mesma grafia para um mesmo conceito;
* evitar sinônimos.

---

# Anexo C — Glossário de Siglas

| Sigla | Significado |
|-------|------------|
| AD | Active Directory |
| API | Application Programming Interface |
| CMDB | Configuration Management Database |
| FAQ | Frequently Asked Questions |
| GWS | Google Workspace |
| IA | Inteligência Artificial |
| ITAM | IT Asset Management |
| ITSM | IT Service Management |
| KCS | Knowledge-Centered Service |
| LDAP | Lightweight Directory Access Protocol |
| LLM | Large Language Model (Modelo de Linguagem de Grande Escala) |
| n8n | Plataforma de Automação e Orquestração de Workflows |
| MFA | Multi-Factor Authentication |
| PITR | Point-In-Time Recovery |
| RAG | Retrieval-Augmented Generation (Recuperação Aumentada por Geração) |
| SLA | Service Level Agreement |
| SSO | Single Sign-On |
| UD | Unidade Descentralizada |
| VPN | Virtual Private Network |
| WAL | Write-Ahead Logging |

---

# Referências Bibliográficas

1. **KCS v6 — Knowledge-Centered Service.** Consortium for Service Innovation. Disponível em: https://www.serviceinnovation.org/kcs/
2. **BookStack Documentation.** Disponível em: https://www.bookstackapp.com/docs/
3. **Qdrant — Vector Database.** Documentação oficial. Disponível em: https://qdrant.tech/documentation/
4. **n8n — Workflow Automation.** Plataforma de orquestração de workflows. Disponível em: https://docs.n8n.io/
5. **Lewis, P. et al. (2020).** *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.* Advances in Neural Information Processing Systems (NeurIPS).
6. **ITIL 4 — IT Infrastructure Library.** AXELOS/PeopleCert. Framework de gerenciamento de serviços de TI.
7. **HDI — Knowledge Management Fundamentals.** Help Desk Institute. Práticas de gestão do conhecimento para Service Desk.