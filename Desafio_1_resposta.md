# Resposta ao desafio (1)

O código é basicamente um programa que ajuda a encontrar o modelo Claude 3 adequado com base em uma característica fornecida pelo usuário.
Para a resolução utilizei **Python**.

## Dicionário de características dos modelos

Primeiro, ele define um dicionário chamado `caracteristicas_modelos`. Este dicionário associa várias características (como “automatizar tarefas”, “pesquisa e desenvolvimento”, etc.) a modelos específicos do Claude 3 (como “Claude 3 Opus”, “Claude 3 Haiku”, “Claude 3 Sonnet”).

~~~ Python

# Dicionário associando características aos modelos Claude 3

caracteristicas_modelos = {
    "automatizar tarefas": "Claude 3 Opus",
    "pesquisa e desenvolvimento": "Claude 3 Opus",
    "resposta rápida e capacidade de resposta quase instantânea": "Claude 3 Haiku",
    "motores de chatbots de lojas": "Claude 3 Haiku",
    "moderação de conteúdo": "Claude 3 Haiku",
    "processamento de tarefas mais básicas": "Claude 3 Haiku",
    "raciocínio cuidadoso": "Claude 3 Sonnet",
    "processamento de dados": "Claude 3 Sonnet",
    "aplicações de vendas": "Claude 3 Sonnet",
    "extração de texto de imagens": "Claude 3 Sonnet",
    "equilíbrio ideal entre inteligência e velocidade": "Claude 3 Sonnet",
}
~~~

## Função para encontrar o modelo

Em seguida, ele define uma função chamada `encontrar_modelo`. Esta função recebe uma característica como entrada (`caracteristica_fornecida`) e verifica se essa característica está presente no dicionário `caracteristicas_modelos`. Se estiver, a função retorna o **modelo correspondente**. Se não estiver, a função retorna a string **“Modelo não encontrado.”**

~~~ Python

# Função para encontrar o modelo correspondente à característica fornecida

def encontrar_modelo(caracteristica_fornecida):
    for caracteristica, modelo in caracteristicas_modelos.items():
        if caracteristica.lower() in caracteristica_fornecida.lower():
            return modelo
    return "Modelo não encontrado."

~~~

## Entrada do usuário

O código então solicita ao usuário para digitar a característica desejada. A entrada do usuário é armazenada na variável `caracteristica_fornecida`.

~~~ Python

# Entrada do usuário - Amigável
caracteristica_fornecida = input("Digite a característica desejada: ")

~~~
ou
~~~ Python

# Entrada do usuário
caracteristica_fornecida = input()

~~~

## Encontrar e imprimir o modelo correspondente

Finalmente, o código chama a função `encontrar_modelo` com a característica fornecida pelo usuário e armazena o resultado na variável `modelo_correspondente`. Em seguida, ele imprime o valor de `modelo_correspondente`, que será o **modelo Claude 3 correspondente** à característica fornecida pelo usuário, ou a string **“Modelo não encontrado”** se a característica não estiver no dicionário.

~~~ Python
# Encontrar e imprimir o modelo correspondente

modelo_correspondente = encontrar_modelo(caracteristica_fornecida)
print(modelo_correspondente)
~~~

## Código completo

~~~ Python

# Dicionário associando características aos modelos Claude 3
caracteristicas_modelos = {
    "automatizar tarefas": "Claude 3 Opus",
    "pesquisa e desenvolvimento": "Claude 3 Opus",
    "resposta rápida e capacidade de resposta quase instantânea": "Claude 3 Haiku",
    "motores de chatbots de lojas": "Claude 3 Haiku",
    "moderação de conteúdo": "Claude 3 Haiku",
    "processamento de tarefas mais básicas": "Claude 3 Haiku",
    "raciocínio cuidadoso": "Claude 3 Sonnet",
    "processamento de dados": "Claude 3 Sonnet",
    "aplicações de vendas": "Claude 3 Sonnet",
    "extração de texto de imagens": "Claude 3 Sonnet",
    "equilíbrio ideal entre inteligência e velocidade": "Claude 3 Sonnet",
}

# Função para encontrar o modelo correspondente à característica fornecida
def encontrar_modelo(caracteristica_fornecida):
    for caracteristica, modelo in caracteristicas_modelos.items():
        if caracteristica.lower() in caracteristica_fornecida.lower():
            return modelo
    return "Modelo não encontrado."

# Entrada do usuário
caracteristica_fornecida = input()

# Encontrar e imprimir o modelo correspondente
modelo_correspondente = encontrar_modelo(caracteristica_fornecida)
print(modelo_correspondente)

~~~
