# Resposta ao desafio (3)


## Dicionário de Modelos

Primeiro, o código cria uma lista chamada `modelos_disponiveis`, que contém três dicionários. Cada dicionário representa um modelo do **Amazon Bedrock**, com campos para `nome`, `pontuacao_desempenho` e `preco_mensal`.


~~~ Python

# Crie uma lista de dicionários representando os três modelos do Amazon Bedrock, com 'nome', 'pontuacao_desempenho' e 'preco_mensal'
modelos_disponiveis = [
    {'nome': 'Claude 3 Opus', 'pontuacao_desempenho': 9, 'preco_mensal': 600},
    {'nome': 'Claude 3 Sonnet', 'pontuacao_desempenho': 8, 'preco_mensal': 450},
    {'nome': 'Claude 3 Haiku', 'pontuacao_desempenho': 7, 'preco_mensal': 350}
]

~~~

## Função para recomendar modelo

A função `recomendar_modelo` recebe uma lista de modelos e um orçamento como parâmetros. Ela é usada para recomendar um modelo baseado no orçamento fornecido.
1. Se o orçamento for inferior a 250, a função retorna None e uma mensagem informando que o orçamento é muito baixo.
2. Em seguida, a função cria uma lista `modelos_dentro_orcamento` que contém apenas os modelos cujo `preco_mensal` é menor ou igual ao orçamento fornecido.
3. Se `modelos_dentro_orcamento` estiver vazio (ou seja, nenhum modelo se encaixa no orçamento), a função encontra o modelo mais próximo do orçamento (mesmo que esteja acima do orçamento) e retorna o nome desse modelo e uma mensagem.
4. Se houver modelos dentro do orçamento, a função encontra o modelo com a maior ‘pontuacao_desempenho’ e retorna o nome desse modelo e uma mensagem.

~~~ Python

def recomendar_modelo(modelos, orcamento):
    # Verifique se o orçamento fornecido é suficiente. Se o orçamento for inferior a 250, implemente a resposta adequada
    if orcamento < 250:
        return None, "Seu orçamento é muito baixo para recomendar um modelo adequado."

    modelos_dentro_orcamento = [modelo for modelo in modelos if modelo['preco_mensal'] <= orcamento]

    # Caso nenhum modelo esteja dentro do orçamento
    if not modelos_dentro_orcamento:
        modelo_mais_proximo = min(modelos, key=lambda x: abs(x['preco_mensal'] - orcamento))
        return modelo_mais_proximo['nome'], "Este modelo está mais próximo do seu orçamento."

    # Caso todos os modelos estejam dentro do orçamento
    melhor_modelo = max(modelos_dentro_orcamento, key=lambda x: x['pontuacao_desempenho'])
    return melhor_modelo['nome'], "Melhor desempenho dentro do seu orçamento."

~~~

## Entrada do usuário

O código então solicita ao usuário para digite o `desempenho`,`velocidade`,`custo` e as `capacidades` desejada. A entrada do usuário é armazenada nas variáveis.

~~~ Python

# Entrada do usuário - Amigável
orcamento_usuario = float(input("Digite seu orçamento: $ "))

~~~
ou
~~~ Python

# Entrada do usuário
orcamento_usuario = float(input())

~~~

## Recomendar e imprimir o modelo correspondente

O código chama a função `recomendar_modelo`, passando a lista `modelos_disponiveis` e o `orcamento_usuario` como argumentos. A função retorna o `modelo_recomendado` e o `motivo` para a recomendação.

Finalmente, o código verifica se um `modelo_recomendado` foi retornado. Se sim, imprime o nome do modelo e o motivo. Se não, imprime apenas o motivo.

~~~ Python
# Chamada da função para recomendar o modelo
modelo_recomendado, motivo = recomendar_modelo(modelos_disponiveis, orcamento_usuario)

# Saída da recomendação
if modelo_recomendado:
    print(modelo_recomendado + ". " + motivo)
else:
    print(motivo)

~~~

## Código completo

~~~ Python

# Crie uma lista de dicionários representando os três modelos do Amazon Bedrock, com 'nome', 'pontuacao_desempenho' e 'preco_mensal'
modelos_disponiveis = [
    {'nome': 'Claude 3 Opus', 'pontuacao_desempenho': 9, 'preco_mensal': 600},
    {'nome': 'Claude 3 Sonnet', 'pontuacao_desempenho': 8, 'preco_mensal': 450},
    {'nome': 'Claude 3 Haiku', 'pontuacao_desempenho': 7, 'preco_mensal': 350}
]

def recomendar_modelo(modelos, orcamento):
    # Verifique se o orçamento fornecido é suficiente. Se o orçamento for inferior a 250, implemente a resposta adequada
    if orcamento < 250:
        return None, "Seu orçamento é muito baixo para recomendar um modelo adequado."

    modelos_dentro_orcamento = [modelo for modelo in modelos if modelo['preco_mensal'] <= orcamento]

    # Caso nenhum modelo esteja dentro do orçamento
    if not modelos_dentro_orcamento:
        modelo_mais_proximo = min(modelos, key=lambda x: abs(x['preco_mensal'] - orcamento))
        return modelo_mais_proximo['nome'], "Este modelo está mais próximo do seu orçamento."

    # Caso todos os modelos estejam dentro do orçamento
    melhor_modelo = max(modelos_dentro_orcamento, key=lambda x: x['pontuacao_desempenho'])
    return melhor_modelo['nome'], "Melhor desempenho dentro do seu orçamento."

# Solicitar orçamento do usuário
orcamento_usuario = float(input())

# Chamada da função para recomendar o modelo
modelo_recomendado, motivo = recomendar_modelo(modelos_disponiveis, orcamento_usuario)

# Saída da recomendação
if modelo_recomendado:
    print(modelo_recomendado + ". " + motivo)
else:
    print(motivo)

~~~
