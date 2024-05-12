# Resposta ao desafio (2)

Este código define uma função chamada `selecionar_modelo` que recebe quatro parâmetros: `desempenho`, `velocidade`, `custo` e `capacidades`. A função é usada para selecionar o modelo mais adequado de um conjunto de modelos baseado nos critérios fornecidos.

## Dicionário de Modelos

Primeiro, a função define um dicionário chamado modelos. Este dicionário contém três modelos diferentes: ‘Claude 3 Opus’, ‘Claude 3 Sonnet’ e ‘Claude 3 Haiku’. Cada modelo tem suas próprias características, que são representadas como um dicionário de valores. As características incluem `desempenho`, `velocidade`, `custo` e uma lista de `capacidades`.


~~~ Python

def selecionar_modelo(desempenho, velocidade, custo, capacidades):
    # Dicionário com as características dos modelos Claude 3
    modelos = {
        'Claude 3 Opus': {'desempenho': 9, 'velocidade': 10, 'custo': 5, 'capacidades': ['Pesquisa', 'Desenvolvimento acelerado']},
        'Claude 3 Sonnet': {'desempenho': 8, 'velocidade': 5, 'custo': 7, 'capacidades': ['Codificação', 'Recuperação de informações']},
        'Claude 3 Haiku': {'desempenho': 7, 'velocidade': 9, 'custo': 6, 'capacidades': ['Velocidade', 'Resumo de dados não estruturados']}
    }

~~~

## Conversão de Capacidades

A função então converte a string de capacidades fornecida em uma lista, dividindo a string em cada vírgula.

~~~ Python

# Convertendo a lista de capacidades de string para lista
capacidades_lista = capacidades.split(', ')

~~~

## Seleção de Modelo

A função então itera sobre cada modelo no dicionário de modelos. Para cada modelo, ela verifica se o desempenho e a velocidade do modelo são maiores ou iguais aos requisitos fornecidos, e se o custo do modelo é menor ou igual ao custo fornecido. Se todas essas condições forem atendidas, a função verifica se todas as capacidades requeridas estão presentes no modelo. Se estiverem, a função retorna uma string indicando que o modelo atual é o modelo recomendado.

**Nenhum Modelo Encontrado**: Se a função passar por todos os modelos sem encontrar um que atenda a todos os critérios, ela retorna uma string indicando que nenhum modelo foi encontrado.

~~~ Python

 # Verificando cada modelo para encontrar o mais adequado
    for modelo, caracteristicas in modelos.items():
        if (caracteristicas['desempenho'] >= desempenho and
            caracteristicas['velocidade'] >= velocidade and
            caracteristicas['custo'] <= custo):
            # Verifica se todas as capacidades requeridas estão nas capacidades do modelo
            if all(cap in caracteristicas['capacidades'] for cap in capacidades_lista):
                return f"O {modelo} é o modelo recomendado."

    return "Nenhum modelo encontrado."

~~~


## Entrada do usuário

O código então solicita ao usuário para digite o `desempenho`,`velocidade`,`custo` e as `capacidades` desejada. A entrada do usuário é armazenada nas variáveis.

~~~ Python

# Entrada do usuário - Amigável
desempenho = int(input("Digite o desempenho: "))
velocidade = int(input("Digite a velocidade: "))
custo = int(input("Digite o custo: "))
capacidades = input("Escreva a capacidade: ")

~~~
ou
~~~ Python

# Entrada do usuário
desempenho = int(input())
velocidade = int(input())
custo = int(input())
capacidades = input()

~~~

## Encontrar e imprimir o modelo correspondente

Finalmente, o código chama a função `selecionar_modelo` com a característica fornecida pelo usuário e imprime o valor do modelo correspondente.

~~~ Python
# Encontrar e imprimir o modelo correspondente
print(selecionar_modelo(desempenho, velocidade, custo, capacidades))

~~~

## Código completo

~~~ Python

def selecionar_modelo(desempenho, velocidade, custo, capacidades):
    # Dicionário com as características dos modelos Claude 3
    modelos = {
        'Claude 3 Opus': {'desempenho': 9, 'velocidade': 10, 'custo': 5, 'capacidades': ['Pesquisa', 'Desenvolvimento acelerado']},
        'Claude 3 Sonnet': {'desempenho': 8, 'velocidade': 5, 'custo': 7, 'capacidades': ['Codificação', 'Recuperação de informações']},
        'Claude 3 Haiku': {'desempenho': 7, 'velocidade': 9, 'custo': 6, 'capacidades': ['Velocidade', 'Resumo de dados não estruturados']}
    }

    # Convertendo a lista de capacidades de string para lista
    capacidades_lista = capacidades.split(', ')

    # Verificando cada modelo para encontrar o mais adequado
    for modelo, caracteristicas in modelos.items():
        if (caracteristicas['desempenho'] >= desempenho and
            caracteristicas['velocidade'] >= velocidade and
            caracteristicas['custo'] <= custo):
            # Verifica se todas as capacidades requeridas estão nas capacidades do modelo
            if all(cap in caracteristicas['capacidades'] for cap in capacidades_lista):
                return f"O {modelo} é o modelo recomendado."

    return "Nenhum modelo encontrado."


# Exemplo de uso da função
desempenho = int(input())
velocidade = int(input())
custo = int(input())
capacidades = input()

# Chamando a função e imprimindo o resultado

print(selecionar_modelo(desempenho, velocidade, custo, capacidades))

~~~

## 

[![Home](https://img.shields.io/badge/-Voltar-e67e22?style=for-the-badge)](https://github.com/omarcosta/Treinando-Desafios-de-Codigos-com-IAs-Generativas/blob/main/README.md)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[![Desafio 2](https://img.shields.io/badge/-Resposta%20ao%20desafio-e67e22?style=for-the-badge)](https://github.com/omarcosta/Treinando-Desafios-de-Codigos-com-IAs-Generativas/blob/main/Desafio_2.md)
