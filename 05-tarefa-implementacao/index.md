# Implementação de tarefas

## Informações gerais

- Capítulo: [Implementação de tarefas](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-05.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Danilo Ladeira de Oliveira Cosme
- matrícula: 20232014040005 

## Respostas dos exercícios

O que é um TCB (Task Control Block), qual sua finalidade e o que ele armazena?
O TCB (Bloco de Controle de Tarefa) é uma estrutura de dados usada pelo sistema operacional para administrar e acompanhar uma tarefa ou processo. Ele armazena informações essenciais como o contexto da tarefa (registradores, ponteiro da pilha, etc.), seu estado atual (pronto, em execução, suspenso), identificadores únicos, recursos em uso (arquivos, conexões de rede) e dados sobre prioridade e tempo de execução. Sua principal função é permitir que o sistema operacional gerencie a troca e retomada de tarefas de maneira eficiente.

Desenhe o gráfico de tempo para a execução do código abaixo, apresente a saída esperada na tela (valores de x) e calcule a duração aproximada da execução.
O diagrama de tempo da execução do código mostra que duas chamadas fork() criam múltiplos processos filhos. Como cada processo incrementa x duas vezes, a saída conterá diferentes valores para x, dependendo de quantas execuções ocorrem. Considerando os sleep(5) presentes no código, o tempo total de execução será próximo de 10 segundos. A tela mostrará várias mensagens do tipo "Valor de x: 1" e "Valor de x: 2", com base no número de processos gerados.

Quantas letras “X” serão exibidas na tela pelo código abaixo?
O programa exibe "X" cada vez que um processo é criado via fork(). Com base na linha de comando a.out 4 3 2 1, cada valor representa o número de processos gerados em sequência. Assim, o total de letras "X" mostradas dependerá do número de forks realizados e suas condições.

O que são threads e qual seu propósito?
Threads são fluxos de execução independentes dentro de um processo, permitindo a execução simultânea de diferentes partes de um programa. Elas são úteis para otimizar o desempenho em tarefas paralelas, como lidar com múltiplas conexões de rede ao mesmo tempo em um servidor.

Quais são os principais prós e contras das threads em relação aos processos?
Vantagens: Threads são mais leves que processos, compartilham memória e arquivos abertos, e a troca de contexto entre elas é mais rápida.
Desvantagens: Como compartilham os mesmos recursos, um erro em uma thread pode afetar todas as outras no processo. Além disso, o compartilhamento de permissões pode gerar vulnerabilidades de segurança.

Cite dois exemplos onde o uso de threads não melhora o desempenho em relação a uma implementação sequencial.
Exemplo 1: Aplicações que realizam cálculos intensivos sem dependência de entrada/saída podem não se beneficiar do uso de threads, pois o tempo de gerenciamento das mesmas pode aumentar o tempo total de execução.
Exemplo 2: Programas que acessam um único recurso compartilhado, como um arquivo, podem sofrer contenção, levando a bloqueios frequentes entre as threads e resultando em um desempenho inferior.

Associe as afirmações a seguir aos seguintes modelos de threads: a) many-to-one (N:1); b) one-to-one (1:1); c) many-to-many (N:M).

(a) a. Tem implementação mais simples e leve.
(b) c. Faz a multiplexação dos threads de usuário em um grupo de threads no nível do núcleo.
(c) b. Pode sobrecarregar o núcleo devido ao grande número de threads gerenciadas.
(d) a. Não permite que um único processo utilize múltiplas CPUs ao mesmo tempo.
(e) c. Possibilita maior concorrência sem sobrecarregar excessivamente o sistema.
(f) a. Normalmente implementado através de bibliotecas.
(g) b. Modelo usado pelo Windows NT e seus sucessores.
(h) a. Se um thread bloquear, todos os outros no mesmo processo também aguardam.
(i) b. Cada thread no nível de usuário possui uma correspondente diretamente gerenciada pelo núcleo.
(j) c. É o modelo mais complexo de implementar.

Comparação das implementações de threads N:1 e 1:1 para o trecho de código abaixo:
a) Desenhe os diagramas de execução:
No modelo N:1, todas as threads são gerenciadas pelo espaço do usuário, e apenas uma thread executa por vez. No modelo 1:1, cada thread no nível do usuário tem um correspondente no nível do núcleo, permitindo que múltiplas threads rodem simultaneamente em diferentes núcleos.

b) Informe as durações aproximadas de execução:
A implementação N:1 será mais lenta, pois não permite execução paralela. Já na 1:1, a execução será mais eficiente, pois múltiplas threads podem rodar ao mesmo tempo.

c) Indique a saída esperada do programa na tela:
A saída mostrará valores de x e y conforme a ordem de execução das threads. No modelo N:1, os valores podem parecer mais ordenados, enquanto no 1:1 pode haver uma ordem mais aleatória devido à execução concorrente.

