
# Funções com Threads em Python

## Ordenando uma Lista

Vamos criar uma função para ordenar uma lista de números. O algoritmo utilizado será o **Selection Sort**.

```python
def ordenar_lista(lista):
    # Itera pela lista
    for i in range(len(lista)):
        # Encontra o menor valor na parte não ordenada da lista
        indice_minimo = i
        for j in range(i+1, len(lista)):
            if lista[indice_minimo] > lista[j]:
                indice_minimo = j
        # Troca o menor valor encontrado com o primeiro valor da parte não ordenada
        lista[i], lista[indice_minimo] = lista[indice_minimo], lista[i]
    return lista
```

## Salvando o Resultado em um Arquivo

Agora, vamos adicionar uma função para salvar o resultado da lista ordenada em um arquivo.

```python
def salvar_em_arquivo(lista, nome_arquivo):
    with open(nome_arquivo, 'w') as f:
        for item in lista:
            f.write(f"{item}\n")
```

## Gerando Números Aleatórios

Para substituir a lista constante, vamos gerar 1000 números aleatórios dentro de um intervalo específico.

```python
import random

def gerar_numeros_aleatorios(n, limite_inferior, limite_superior):
    return [random.randint(limite_inferior, limite_superior) for _ in range(n)]
```

## Utilizando Threads

Agora, vamos executar as funções acima usando threads. A ideia é rodar a geração de números, a ordenação e a gravação em arquivo simultaneamente.

```python
import threading

def principal():
    # Gera 1000 números aleatórios entre 1 e 1000
    numeros = gerar_numeros_aleatorios(1000, 1, 1000)
    
    # Cria uma thread para ordenar a lista
    thread_ordem = threading.Thread(target=ordenar_lista, args=(numeros,))
    
    # Inicia a thread de ordenação
    thread_ordem.start()
    
    # Aguarda a finalização da thread de ordenação
    thread_ordem.join()
    
    # Salva a lista ordenada em um arquivo
    salvar_em_arquivo(numeros, 'lista_ordenada.txt')
    print("A lista ordenada foi salva no arquivo 'lista_ordenada.txt'.")

# Executa a função principal
principal()
```

## Estados das Threads em Python

As threads em Python podem passar por diferentes estados durante sua execução. Aqui estão os principais estados:

1. **Novo (New)**: A thread foi criada, mas ainda não foi iniciada.
2. **Executável (Runnable)**: A thread está pronta para ser executada e está aguardando seu turno para ser executada pelo processador.
3. **Em Execução (Running)**: A thread está sendo executada ativamente pelo processador.
4. **Em Espera (Waiting)**: A thread está aguardando por algum recurso ou evento, como a liberação de um bloqueio.
5. **Bloqueada (Blocked)**: A thread está impedida de continuar até que uma condição específica seja atendida.
6. **Terminada (Terminated)**: A thread finalizou sua execução.

Esses estados ajudam a gerenciar e controlar o comportamento das threads no Python, otimizando o uso dos recursos de forma eficiente.