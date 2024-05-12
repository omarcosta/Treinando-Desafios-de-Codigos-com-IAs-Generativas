# Desafios de Códigos (3) - Treinando IAs Generativas

### Descrição
Você foi contratado para desenvolver uma lista de dicionários chamado `modelos_disponiveis` contendo os modelos de inteligência artificial (IA) da Amazon Bedrock, dentro da lista crie três dicionários, sendo, `nome`, `pontuacao_desempenho` e `preco_mensal`, cada um deles representa um modelo disponível para recomendação e suas características.

Em seguida crie uma função chamada `recomendar_modelo` e receba dois parâmetros que será modelos e orçamento, que representa uma lista de modelos e o orçamento do usuário em unidades monetárias. Dentro da função recomendar_modelo verifique se o orçamento fornecido é suficiente para recomendar algum modelo. Se o orçamento for inferior a 250 unidades monetárias, a função retorna uma tupla com dois elementos:

1. "None": indicando que nenhum modelo pode ser recomendado.
2. Uma mensagem de aviso informando que o orçamento é muito baixo para recomendar um modelo adequado..

O objetivo geral do desafio é selecionar o melhor modelo que é escolhido com base no orçamento, priorizando modelos com preço mais próximo ao orçamento fornecido pelo usuário.

Detalhes dos Modelos:
- **Modelo:** Claude 3 Opus. **Desempenho:** 9. **Preço mensal: $** 600;
- **Modelo:** Claude 3 Sonnet. **Desempenho:** 8. **Preço mensal: $** 450;
- **Modelo:** Claude 3 Haiku. **Desempenho:** 7. **Preço mensal: $** 350;

### Entrada
O usuário deve fornecer os detalhes seu orçamento para que seja avaliado o melhor modelo com base no seu orçamento pelo preço mensal e desempenho.

### Saída
Com base nos modelos fornecidos e no orçamento especificado, a função deve recomendar o modelo adequado conforme o seu orçamento. O melhor modelo sugerido deve ser escolhido com base no orçamento, priorizando modelos com preço mais próximo ao orçamento fornecido pelo usuário. Caso o orçamento seja menor do que 250, retorne uma mensagem informando: "Se orçamento é muito baixo para recomendar um modelo adequado."

### Exemplos
A tabela abaixo apresenta exemplos com alguns dados de entrada e suas respectivas saídas esperadas. Certifique-se de testar seu programa com esses exemplos e com outros casos possíveis.

| Dados de entrada  | Saída |
| ------------- | ------------- |
| 300 | Claude 3 Haiku. Este modelo está mais próximo do seu orçamento. |
| 700 | Claude 3 Opus. Melhor desempenho dentro do seu orçamento. |
| 550 | Claude 3 Sonnet. Melhor desempenho dentro do seu orçamento. |
| 249 | Seu orçamento é muito baixo para recomendar um modelo adequado. |
