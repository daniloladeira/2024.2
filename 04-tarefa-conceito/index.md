# Conceito de tarefas

## Informações gerais

- Capítulo: [Conceito de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-04.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Danilo Ladeira de Oliveira Cosme
- matrícula: 20232014040005

## Respostas dos exercícios

### 1. O que é time sharing e qual sua relevância em um sistema operacional?

Time sharing é um método no qual o processador divide seu tempo entre múltiplos processos, atribuindo pequenas porções de tempo (quantum) para cada um. Isso proporciona a sensação de execução simultânea das tarefas, otimizando o uso do sistema, especialmente em ambientes multitarefa. A relevância do time sharing está em garantir que todos os processos tenham acesso equilibrado ao processador, evitando que uma única tarefa monopolize os recursos do sistema.

---

### 2. Como é definida a duração de um quantum de processamento?

A escolha da duração do quantum de processamento é baseada no equilíbrio entre responsividade e eficiência do sistema. Se o quantum for muito curto, haverá um grande custo com a alternância de tarefas (overhead). Se for muito longo, a interação do sistema será comprometida, pois os processos terão que aguardar mais tempo para serem retomados. Fatores como o tipo de aplicação, prioridade da tarefa e características gerais do sistema influenciam na definição desse tempo.

---

### 3. Complete o diagrama com a transição de estado ausente (t6) e descreva cada estado e transição.

A transição t6 ausente no diagrama é a passagem do estado **S (suspensa) para P (pronta)**. Essa mudança ocorre quando o evento ou recurso pelo qual a tarefa estava aguardando se torna disponível, permitindo que ela retorne à fila de processos prontos para execução.

---

### 4. Avaliação das possíveis transições entre estados de tarefas:

- **E → P**: **Possível**. Acontece quando o tempo de processamento da tarefa se esgota, fazendo com que ela volte para a fila de prontas.
  
- **E → S**: **Possível**. Ocorre quando a tarefa precisa esperar por um recurso externo, como uma operação de entrada/saída.

- **S → E**: **Possível**. Quando o recurso necessário fica disponível, permitindo que a tarefa retorne à execução.

- **P → N**: **Impossível**. Uma vez criada, uma tarefa não pode retornar ao estado de "nova".

- **S → T**: **Possível**. Acontece quando uma tarefa suspensa é finalizada ou interrompida.

- **E → T**: **Possível**. Ocorre quando a tarefa conclui sua execução ou é terminada pelo sistema.

- **N → S**: **Impossível**. Antes de ser suspensa, uma tarefa precisa estar no estado pronto ou em execução.

- **P → S**: **Possível**. Se uma tarefa pronta precisa esperar por um recurso antes de ser processada, ela pode ser suspensa.

---

### 5. Associação das afirmações aos estados no ciclo de vida das tarefas:

- **[N]** O código da tarefa está sendo carregado na memória.  
- **[P]** As tarefas são organizadas conforme suas prioridades.  
- **[S]** A tarefa sai desse estado quando solicita uma operação de entrada/saída.  
- **[T]** Os recursos utilizados pela tarefa são liberados para o sistema.  
- **[P]** A tarefa retorna para esse estado ao concluir seu quantum de processamento.  
- **[P]** A única necessidade da tarefa nesse estado é o processador para ser executada.  
- **[S]** A espera por um semáforo já em uso pode colocar a tarefa nesse estado.  
- **[E]** A tarefa pode iniciar novas tarefas enquanto está nesse estado.  
- **[E]** Existe uma tarefa nesse estado para cada processador do sistema.  
- **[S]** A tarefa permanece nesse estado enquanto aguarda um evento externo.
