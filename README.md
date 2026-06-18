# Desafio DIO - Miniguia de Estudos: Fundamentals of Software Testing

Repositório criado para o primeiro desafio de projeto do **Bootcamp Bradesco - GenAI, Dados e Cyber** na plataforma [DIO](https://www.dio.me/). O objetivo principal é aplicar o conceito de aprendizagem ativa utilizando o Google NotebookLM como ferramenta de curadoria, síntese e organização do conhecimento.

---

## Contexto e Objetivos

* **Tema Escolhido para o Caderno Temático:** Testes de Software (*Fundamentals of Software Testing*).
* **Justificativa e Objetivo de Estudo:** Como profissional atuante na área de desenvolvimento e garantia de qualidade, o objetivo deste material é aprofundar os conhecimentos conceituais e teóricos sobre testes, alinhando a prática diária às metodologias e padrões consolidados do mercado para elevar o nível técnico das entregas.

---

## Curadoria de Fontes

Para alimentar o NotebookLM e garantir a precisão técnica das respostas, foi utilizada a seguinte base documental central:

1.  **Fundamentals of Software Testing: A Complete Guide** - Documento base contendo as diretrizes, princípios de testes, tipologias e ciclo de vida de QA.

---

## Engenharia de Prompts

Registro das interações com a IA, documentando a evolução das perguntas para extrair insights precisos sobre a engenharia de testes a partir da fonte fornecida.

### Prompt de Teste 1 
* **Prompt enviado:** "Explique o que são testes de regressão e por que eles são importantes."
* **Resultado obtido:** Os **testes de regressão são avaliações executadas sempre que o software sofre alguma modificação**, seja pela adição de uma nova funcionalidade, uma melhoria técnica ou a correção de um defeito (bug) encontrado em uma versão anterior. O propósito fundamental dessa prática é **garantir que essas mudanças não tenham introduzido novos defeitos ou "quebrado" recursos que já funcionavam corretamente**. Em sua essência, o teste de regressão visa certificar que o sistema continua fazendo perfeitamente o que ele costumava fazer ontem.

A mecânica do teste de regressão geralmente consiste em **reexecutar um subconjunto ou a totalidade dos casos de teste já existentes** e projetados para as versões anteriores do software. 

A importância dessa camada de testes é imensa para a garantia da qualidade devido aos seguintes fatores:

*   **Alterações são altamente propensas a novos erros:** A prática da engenharia de software demonstra que as correções de bugs e as modificações em um código já existente tendem a ser muito mais propensas a gerar novos erros do que o processo de escrita do código original. Uma correção que parece válida e pontual pode facilmente gerar um efeito colateral indesejado, introduzindo uma falha totalmente nova.
*   **Contenção do efeito cascata:** Especialmente em sistemas complexos, até mesmo uma modificação de configuração que parece menor pode impactar dados e corromper módulos do sistema que são completamente desvinculados da mudança que está sendo implementada.
*   **Proteção do investimento em testes:** Uma das diretrizes fundamentais da qualidade é evitar "casos de teste descartáveis". O esforço empregado para desenhar testes no passado é preservado. Sem a reexecução estruturada desses testes antigos, as falhas que corrompem componentes que antes eram funcionais passariam totalmente despercebidas pela equipe e chegariam ao usuário final.

**O Papel Crítico da Automação nos Testes de Regressão**

Como os pacotes de regressão precisam ser executados de forma frequente e repetitiva a cada novo *release* ou solicitação de mudança, realizá-los de forma exclusivamente manual torna-se um gargalo exaustivo e caro em termos de recursos. Por isso, o teste de regressão é o principal e mais adotado caso de uso para a **automação de testes**.

Ao construir **suítes de regressão abrangentes e automatizadas**, a equipe de engenharia ganha uma rede de segurança que fornece feedback imediato sobre qualquer ruptura introduzida por uma nova linha de código. Em ambientes Ágeis e de Integração/Entrega Contínua (CI/CD), a automação da regressão elimina o gargalo da verificação manual e permite que as equipes implantem novos pacotes em produção com altíssima frequência e baixíssimo risco.
* **Pontos de melhoria:** A resposta precisava de maior profundidade técnica e correlação com o ciclo de vida do software documentado na fonte.

### Prompt de Teste 2
* **Prompt enviado:** "Com base estrita na fonte fornecida, aja como um Engenheiro de QA Sênior. Explique a estratégia de testes de regressão, diferenciando-a de testes de fumaça (Smoke Tests). Estruture a resposta em tópicos e cite as referências das seções do documento."
* **Resultado obtido:** Como Engenheiro de QA Sênior, é um prazer detalhar como estruturamos nossas estratégias de qualidade abordando os testes de regressão e diferenciando-os dos testes de fumaça (*Smoke Tests*). Ambos são componentes vitais, mas atuam de formas diferentes no ciclo de vida de desenvolvimento.

Abaixo, detalho a estratégia e a diferença entre eles com base na literatura da área:

### 1. Estratégia de Testes de Regressão

O teste de regressão é uma avaliação realizada sempre que o software sofre alguma modificação, seja a implementação de uma nova funcionalidade ou a correção de um defeito encontrado em uma versão anterior. 

A estratégia de testes de regressão baseia-se nos seguintes pilares:
*   **Garantia contra Efeitos Colaterais:** O objetivo central da regressão é assegurar que as mudanças de código inseridas no sistema não introduziram novos defeitos nem causaram efeitos adversos ou não intencionais no comportamento das funcionalidades que já operavam corretamente. 
*   **Reexecução de Casos de Teste:** Uma abordagem primária consiste em reexecutar os casos de teste já existentes que foram projetados para as versões anteriores daquele software. Ele mimetiza o teste funcional validando o fluxo do usuário após as mudanças em produção.
*   **Foco na Automação:** Por ser uma atividade de repetição constante a cada lançamento subsequente do sistema, o teste de regressão é o candidato ideal para a automação de testes. A automação reduz o esforço e o custo elevados que testes manuais exigiriam, permitindo implantar alterações na produção de forma mais frequente e com menor risco. Suítes de regressão automatizadas abrangentes devem rodar frequentemente para detectar disrupções com rapidez.
*   **Otimização de Esforços (Test Impact Analysis):** Em ambientes modernos, ao invés de rodar toda a suíte de testes de regressão cegamente, os engenheiros otimizam o processo executando prioritariamente cenários críticos de negócios afetados pelo código. Isso pode ser feito através de técnicas de Análise de Impacto de Teste (TIA), que mapeiam e filtram a regressão com base nos *commits* recentes.

### 2. Testes de Fumaça (*Smoke Tests*)

Os testes de fumaça atuam de maneira mais pontual e anterior na validação da estabilidade sistêmica.
*   **Filtro Inicial:** O *smoke testing* é uma verificação rápida e superficial que passa pelas funções mais críticas, essenciais ou "core" do sistema recém-compilado ou recém-implantado.
*   **Validação de Estabilidade:** Sua finalidade é confirmar, de forma expedita, se a *build* do software está estável o suficiente para justificar e suportar os próximos procedimentos de testes mais profundos. Se a função principal falhar no teste de fumaça, significa que o sistema "quebrou" em um nível fundamental, poupando a equipe de perder tempo com testes detalhados até que o problema básico seja corrigido.

### 3. Principais Diferenças (Regressão vs. Fumaça)

Para esclarecer a diferença de escopo e aplicação prática no dia a dia do QA:
*   **Profundidade:** O teste de fumaça é superficial (um teste rápido ou "*shallow*") voltado apenas para o núcleo do sistema. O teste de regressão é aprofundado e minucioso, procurando anomalias em todas as ramificações do sistema que podem ter sido afetadas por uma mudança.
*   **Momento de Aplicação:** O teste de fumaça é usado imediatamente **antes** de os procedimentos de testes reais serem ajustados, atuando como uma porta de entrada para a *build*. Já a regressão acontece **após** a aplicação de mudanças, correções ou novas implementações para confirmar que nenhuma parte pré-existente foi corrompida no processo.

### Aprendizados
* **Dificuldade encontrada:** Ao solicitar cenários de automação, a IA tendeu a usar termos genéricos da internet em vez de focar estritamente na metodologia explicada no guia fornecido.
* **Solução aplicada:** Foi aplicada uma restrição explícita no prompt exigindo que a resposta fosse baseada única e exclusivamente no material anexado.

---

## 📖 Miniguia de Estudo

### 1. Resumos Estruturados do Assunto
O material *Fundamentals of Software Testing: A Complete Guide* estabelece a base teórica e metodológica necessária para garantir a qualidade de artefatos de software durante todo o seu ciclo de vida. Abaixo estão os tópicos centrais consolidados:

#### A. Os 7 Princípios dos Testes de Software
Os testes são guiados por regras fundamentais que alinham as expectativas do negócio à realidade técnica:
1. **Os testes mostram a presença de defeitos, não a ausência:** Testar reduz a probabilidade de falhas ocultas, mas não prova que o software está 100% livre de erros.
2. **Testes exaustivos são impossíveis:** Testar todas as combinações de dados e caminhos lógicos é inviável. A estratégia deve focar em gerenciamento de riscos e priorização.
3. **Testes antecipados (Early Testing):** Iniciar as atividades de QA o quanto antes no ciclo de vida de desenvolvimento (SDLC) reduz drasticamente o custo de correção de bugs.
4. **Agrupamento de defeitos (Defect Clustering):** Geralmente, a maior parte dos bugs se concentra em um número pequeno de módulos (aplicação do Princípio de Pareto / Regra 80/20).
5. **Paradoxo do Pesticida:** Se os mesmos testes forem repetidos continuamente, eles deixarão de encontrar novos defeitos. Os cenários de testes devem ser revisados e atualizados constantemente.
6. **Teste depende do contexto:** O modo como testamos um e-commerce difere completamente de como testamos um software médico ou um sistema bancário.
7. **A ilusão da ausência de erros:** Encontrar e corrigir defeitos não ajuda se o sistema construído for inutilizável ou não atender às reais necessidades do usuário.

### 2. Glossário 
* **Testes de Caixa Preta:** Técnica de teste baseada estritamente nos requisitos e especificações, sem olhar o código-fonte interno.
* **Testes de Caixa Branca:** Técnica que avalia a estrutura interna, o design e o fluxo lógico do código do software.
* **Critérios de Aceite:** Condições que o software deve atender para ser aceito pelo usuário ou cliente.

### 3. Prompts Reutilizáveis para Revisão Técnica
Abaixo estão os comandos estruturados criados durante este desafio que podem ser copiados e colados no NotebookLM para futuras revisões:

* **Prompt 1:** "Aja como um Tech Lead especialista em QA. Com base na fonte 'Fundamentals of Software Testing', gere 3 cenários de testes complexos para um fluxo de e-commerce, aplicando as técnicas de Particionamento de Equivalência e Análise de Valor Limite."
* **Prompt 2:** "Gere um simulado de 5 questões de múltipla escolha focado nos 7 Princípios de Testes de Software descritos no material. Após eu responder, forneça o gabarito comentado justificando com trechos da fonte."

---

## 🛠️ Tecnologias Utilizadas

* Google NotebookLM
* GitHub
* Markdown para documentação técnica

---

## 🙋‍♂️ Autor

* Marcos Vinícius Silva
* [Meu LinkedIn](https://www.linkedin.com/in/marcoscv71/)