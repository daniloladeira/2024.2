# Escalonamento de tarefas

## Informações gerais

- Capítulo: [Escalonamento de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-06.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: 
- matrícula: 

## Respostas dos exercícios

## 1. O que é o escalonamento round-robin? Dê um exemplo.
O escalonamento round-robin é um algoritmo de escalonamento preemptivo que distribui o tempo do processador de forma igualitária entre todas as tarefas prontas. Cada tarefa recebe um intervalo fixo de tempo (quantum). Caso a tarefa não termine dentro desse intervalo, ela volta para o final da fila de prontas, e o processador é alocado para a próxima tarefa. Por exemplo, com três tarefas: t1, t2 e t3, e um quantum de 2 segundos, o processador executaria t1 por 2 segundos, depois t2 por 2 segundos, seguido de t3, retornando para t1 depois que todas as tarefas tiverem sido executadas.

## 2. Em um sistema de tempo compartilhado com quantum tq e tempo de troca de contexto ttc, e com tarefas de entrada/saída que utilizam, em média, p% do seu quantum, defina a eficiência E do sistema como uma função de tq, ttc e p.
A eficiência E do sistema pode ser definida como a fração do tempo em que o processador está sendo utilizado para executar as tarefas, em vez de realizar trocas de contexto. A fórmula para calcular a eficiência seria:  
E = (p * tq) / (p * tq + ttc)  
Ou seja, quanto maior for o valor de p e de tq em comparação com o tempo de troca de contexto ttc, maior será a eficiência do sistema.

## 3. O que é a técnica de aging? Para que serve e como funciona?
A técnica de aging é um método usado para evitar que tarefas de baixa prioridade fiquem bloqueadas em sistemas de escalonamento por prioridade. Ela funciona aumentando gradualmente a prioridade de uma tarefa conforme ela permanece na fila de prontas sem ser executada. Quanto mais tempo uma tarefa espera, mais sua prioridade aumenta, garantindo que eventualmente ela receba a chance de ser executada. Isso assegura que todas as tarefas tenham uma oportunidade de execução, mesmo em sistemas com muitas tarefas de alta prioridade.

## 4. No algoritmo de envelhecimento descrito na Seção 6.4.6, o que seria necessário alterar para suportar uma escala de prioridades negativa?
Para adaptar o algoritmo de envelhecimento a uma escala de prioridades negativa, seria necessário modificar a função de envelhecimento para diminuir a prioridade ao longo do tempo, em vez de aumentá-la. Assim, quanto mais tempo uma tarefa permanecer na fila de prontas, menor seria sua prioridade negativa, aumentando suas chances de ser escolhida para execução.

## 5. A tabela abaixo representa um conjunto de tarefas prontas para utilizar um processador:

| Tarefa   | t1 | t2 | t3 | t4 | t5 |
|----------|----|----|----|----|----|
| Ingresso | 0  | 0  | 3  | 5  | 7  |
| Duração  | 5  | 4  | 5  | 6  | 4  |
| Prioridade | 2 | 3  | 5  | 9  | 6  |

### Represente graficamente a sequência de execução das tarefas e calcule os tempos médios de vida (turnaround time) e de espera (waiting time) para as seguintes políticas de escalonamento:

#### (a) FCFS cooperativa
Na política FCFS (First-Come-First-Served), as tarefas são executadas na ordem em que chegam. A sequência de execução seria: t1 → t2 → t3 → t4 → t5. O tempo de vida e o tempo de espera são calculados com base nessa ordem.

#### (b) SJF cooperativa
No algoritmo SJF (Shortest Job First) cooperativo, as tarefas mais curtas são executadas primeiro. A sequência seria: t2 → t5 → t1 → t3 → t4.

#### (c) SJF preemptiva (SRTF)
Na versão preemptiva do SJF, uma tarefa de menor duração pode interromper uma tarefa em andamento. Isso faria a sequência de execução mudar à medida que novas tarefas com menor duração entram no sistema.

#### (d) PRIO cooperativa
No algoritmo PRIO cooperativo, a tarefa com maior prioridade é executada primeiro. A sequência seria: t4 → t5 → t3 → t2 → t1.

#### (e) PRIO preemptiva
Na versão preemptiva do PRIO, uma tarefa com maior prioridade pode interromper outra tarefa. A sequência de execução seria ajustada conforme a chegada das tarefas com maior prioridade.

#### (f) RR com tq = 2, sem envelhecimento
No escalonamento Round-Robin, cada tarefa recebe 2 segundos de CPU, e a execução segue em ciclos, alternando entre as tarefas. A sequência seria: t1 → t2 → t3 → t4 → t5, com o revezamento das tarefas conforme seus tempos de execução.

## 6. Agora, considere a tabela a seguir:

| Tarefa   | t1 | t2 | t3 | t4 | t5 |
|----------|----|----|----|----|----|
| Ingresso | 0  | 0  | 1  | 7  | 11 |
| Duração  | 5  | 6  | 2  | 6  | 4  |
| Prioridade | 2 | 3  | 4  | 7  | 9  |

### A sequência de execução e os tempos de turnaround e espera podem ser calculados para cada política de escalonamento listada acima, considerando a ordem de ingresso, duração e prioridade das tarefas.
