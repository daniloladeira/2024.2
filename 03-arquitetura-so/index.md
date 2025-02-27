# Arquiteturas de Sistemas Operacionais

## Informações gerais

- Capítulo: [Arquitetura de SO](https://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=socm:socm-03.pdf)
- Disciplina: *sistemas operacionais*
- Livro: [Sistemas Operacionais: Conceitos e Mecanismos](https://wiki.inf.ufpr.br/maziero/doku.php?id=socm:start)

## Aluno

- nome: Danilo Ladeira de Oliveira Cosme
- matrícula: 20232014040005

## Respostas dos exercícios

### 1. Tabela de Benefícios e Deficiências das Principais Arquiteturas de Sistemas Operacionais

| Arquitetura       | Benefícios | Deficiências |
|-------------------|-----------|-------------|
| **Monolítica**   | Alto desempenho, comunicação direta com os componentes do sistema, implementação inicial relativamente simples | Baixa modularidade, manutenção complexa, falhas podem impactar todo o sistema |
| **Micronúcleo**  | Melhor modularidade, maior flexibilidade, robustez (falhas afetam apenas o serviço específico) | Desempenho inferior devido ao uso intensivo de troca de mensagens |
| **Em Camadas**   | Organização estruturada, facilita atualizações e manutenção | Pode reduzir o desempenho, dificuldades na separação de funcionalidades interdependentes |
| **Híbrida**      | Equilibra vantagens das arquiteturas monolítica e micronúcleo, melhora o desempenho sem perder modularidade | Design mais complexo, pode apresentar conflitos entre características distintas |
| **Máquinas Virtuais** | Permite execução simultânea de múltiplos sistemas, oferece isolamento e segurança | Desempenho inferior comparado à execução nativa, depende do hipervisor |
| **Contêineres**  | Isolamento eficiente de processos, melhor uso de recursos do sistema | Menos seguro que hipervisores de sistema, compartilha o mesmo núcleo do SO |
| **Exonúcleo**    | Excelente desempenho, cada aplicação pode definir suas próprias abstrações | Desenvolvimento complexo, ausência de abstrações padrão de SO |
| **Uninúcleo**    | Alta eficiência, adequado para ambientes de nuvem, estrutura compacta | Pouca flexibilidade, difícil reutilização em diferentes contextos |

---

### 2. O Linux é Monolítico ou Micronúcleo?

O Linux é considerado um sistema **monolítico**. Apesar de possuir "tarefas de núcleo" semelhantes aos gerentes de sistemas micronúcleo, sua arquitetura permite que todos os componentes do núcleo interajam diretamente, sem a necessidade de troca de mensagens. Esse acesso direto contribui para o alto desempenho do sistema, uma característica típica dos núcleos monolíticos.

---

### 3. Correção das Afirmações Sobre Arquiteturas de Sistemas Operacionais

- **a) Incorreta** – Uma máquina virtual de sistema possibilita a execução de um sistema operacional completo, enquanto máquinas virtuais de aplicação são voltadas para executar uma única aplicação dentro de um ambiente controlado, como no caso da JVM (Java Virtual Machine).
  
- **b) Correta** – Um hipervisor convidado opera sobre um sistema operacional hospedeiro, funcionando como uma camada de virtualização.

- **c) Incorreta** – Em arquiteturas **micronúcleo**, os componentes principais operam fora do núcleo e interagem por meio de troca de mensagens, diferentemente de módulos interligados dentro do próprio núcleo.

- **d) Incorreta** – Núcleos **monolíticos** não são reconhecidos por sua robustez e facilidade de manutenção. Pelo contrário, sua manutenção pode ser trabalhosa, e uma falha em um único módulo pode comprometer todo o sistema.

- **e) Correta** – Em sistemas **micronúcleo**, as chamadas de sistema são processadas através de trocas de mensagens, pois os serviços operam separadamente do núcleo central.

