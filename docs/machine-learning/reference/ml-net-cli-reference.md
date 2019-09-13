---
title: O comando auto-train na ferramenta de CLI do ML.NET
description: Visão geral, exemplos e referência para o comando de treinamento automático na ferramenta de CLI do ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929194"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>O comando 'auto-train' no ML.NET

> [!NOTE]
> Este tópico refere-se à CLI do ML.NET e ao AutoML do ML.NET, que estão atualmente em Versão Prévia. O material pode estar sujeito a alterações.

O comando `auto-train` é o principal comando fornecido pela ferramenta de CLI do ML.NET. O comando permite que você gere um modelo do ML.NET de boa qualidade (arquivo zip de modelo serializado) mais o código C# de exemplo para executar/pontuar esse modelo. Além disso, o código C# para criar/treinar esse modelo também é gerado para que você possa pesquisar qual algoritmo e configurações ele está usando para esse "melhor modelo" gerado.

Você pode gerar esses ativos de seus próprios conjuntos de dados sem codificação por conta própria, portanto, ele também melhorará a sua produtividade, mesmo se você já conhecer o ML.NET.

Atualmente, as tarefas de ML compatíveis com a CLI do ML.NET são:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Futuro: Outra tarefas aprendizado de máquina, tais como
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Exemplo de uso no prompt de comando:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

O comando `mlnet auto-train` gera os seguintes ativos:

- Um modelo serializado. zip ("melhor modelo") pronto para uso.
- Código C# para a execução/pontuação que gerou o modelo (para fazer previsões em seus aplicativos do usuário final com esse modelo).
- Código C# com o código de treinamento usado para gerar esse modelo (fins de aprendizado).

Os primeiros dois ativos podem ser usados diretamente em seus aplicativos de usuário final (aplicativo Web ASP.NET Core, serviços, aplicativo da área de trabalho etc.) para fazer previsões com esse modelo de ML gerado.

O terceiro ativo, o código de treinamento, mostra o que o código de API do ML.NET foi usado pela CLI para treinar o modelo gerado, portanto, você pode investigar quais treinador/algoritmo e hiperparâmetros específicos foram selecionados pela CLI e pelo mecanismo de AutoML do ML.NET.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>O comando 'auto-train' usa o mecanismo de AutoML

A CLI usa o mecanismo de AutoML do ML.NET (pacote do NuGet) para pesquisar com inteligência para os modelos de melhor qualidade, conforme mostrado no diagrama a seguir:

![imagem](./media/ml-net-automl-working-diagram.png "Mecanismo AutoML funcionando dentro da CLI do ML.NET")

Ao executar a ferramenta de CLI do ML.NET com o comando 'auto-train', você verá a ferramenta tentar muitas iterações com algoritmos e combinações de configuração diferentes.

## <a name="reference-for-auto-train-command"></a>Referência do comando 'auto-train'

## <a name="examples"></a>Exemplos

Comando mais simples da CLI para um problema de classificação binária (o AutoML precisará inferir a maior parte da configuração dos dados fornecidos):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Outro comando simples da CLI para um problema de regressão:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Crie e treine um modelo de classificação binária com um conjunto de dados de treinamento, um conjunto de dados de teste e ainda mais argumentos explícitos de personalização:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Nome

`mlnet auto-train` – Treina vários modelos ('n' iterações) com base no conjunto de dados fornecido e, finalmente, seleciona o melhor modelo, salva-o como um arquivo zip serializado e gera o código C# relacionado para pontuação e treinamento.

## <a name="synopsis"></a>Sinopse

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Opções de entrada inválidas devem fazer com que a ferramenta de CLI emita uma lista de entradas válidas e uma mensagem de erro explicando qual argumento está ausente, se esse for o caso.

## <a name="options"></a>Opções

 ----------------------------------------------------------

`--task | --mltask | -T` (string)

Uma única cadeia de caracteres fornecendo o problema de ML a resolver. Por exemplo, qualquer uma das tarefas a seguir (a CLI eventualmente dará suporte a todas as tarefas compatíveis com o AutoML):

- `regression` – escolha se o modelo do ML será usado para prever um valor numérico
- `binary-classification` – escolha se o resultado do modelo de ML terá dois valores boolianos categóricos possíveis (0 ou 1).
- `multiclass-classification` – escolha se o resultado do modelo de ML terá vários valores boolianos categóricos possíveis.

Em versões futuras, tarefas de ML e cenários como `recommendations`, `clustering` e `ranking` serão compatíveis.

 Uma tarefa de ML deve ser fornecida neste argumento.

 ----------------------------------------------------------

`--dataset | -d` (string)

Esse argumento fornece o caminho do arquivo para uma das seguintes opções:

- *A: O arquivo de conjunto de dados inteiro:* Se essa opção for usada e o usuário não estiver fornecendo `--test-dataset` e `--validation-dataset`, as abordagens de validação cruzada (k vezes etc.) ou de divisão de dados automatizada serão usadas internamente para validar o modelo. Nesse caso, o usuário precisará apenas fornecer o caminho do arquivo do conjunto de dados.

- *B: O arquivo de conjunto de dados de treinamento:* Se o usuário também estiver fornecendo conjuntos de dados para a validação de modelo (usando `--test-dataset` e, opcionalmente `--validation-dataset`), então o argumento `--dataset` significará ter apenas o "conjunto de dados de treinamento". Por exemplo, ao usar uma abordagem de 80-20% para validar a qualidade do modelo e obter métricas de precisão, o "conjunto de dados treinamento" terá 80% dos dados e o "conjunto de dados de teste" terá 20% dos dados.

----------------------------------------------------------

`--test-dataset | -t` (string)

Caminho do arquivo que aponta para o arquivo de conjunto de dados de teste, por exemplo, ao usar uma abordagem de 80-20% ao realizar validações regulares para obter métricas de precisão.

Ao usar `--test-dataset`, `--dataset` também é necessária.

O argumento `--test-dataset` é opcional, a menos que o --validation-dataset seja usado. Nesse caso, o usuário precisa usar os três argumentos.

----------------------------------------------------------

`--validation-dataset | -v` (string)

Caminho do arquivo apontando para o arquivo de conjunto de dados de validação. O conjunto de dados de validação é opcional em qualquer caso.

Se usar um `validation dataset`, o comportamento deverá ser:

- Os argumentos `test-dataset` e `--dataset` também são necessários.

- O conjunto de dados `validation-dataset` é usado para estimar o erro de previsão para a seleção de modelo.

- O `test-dataset` é usado para a avaliação do erro de generalização do modelo final escolhido. O ideal é que o conjunto de teste seja mantido em um "cofre" e seja levado somente no final da análise de dados.

Basicamente, ao usar um `validation dataset` mais o `test dataset`, a fase de validação é dividida em duas partes:

1. Na primeira parte, você apenas examina seus modelos e seleciona a abordagem com melhor desempenho usando os dados de validação (=validation)
2. Em seguida, você pode estimar a precisão da abordagem selecionada (=test).

Portanto, a separação dos dados pode ser 80/10/10 ou 75/15/10. Por exemplo:

- O arquivo `training-dataset` deve ter 75% dos dados.
- O arquivo `validation-dataset` deve ter 15% dos dados.
- O arquivo `test-dataset` deve ter 10% dos dados.

Em qualquer caso, essas porcentagens serão decididas pelo usuário usando a CLI que fornecerá os arquivos já dividido.

----------------------------------------------------------

`--label-column-name | -n` (string)

Com este argumento, uma coluna de destino/objetivo específica (a variável que você deseja prever) pode ser especificada usando o nome da coluna definido no cabeçalho do conjunto de dados.

Esse argumento é usado somente para tarefas de ML supervisionadas, tais como um *problema de classificação*. Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.

----------------------------------------------------------

`--label-column-index | -i` (int)

Com este argumento, uma coluna de destino/objetivo específico (a variável que você deseja prever) pode ser especificada usando o índice numérico da coluna no arquivo do conjunto de dados (os valores de coluna de índice começam em 1).

*Observação:* Se o usuário também estiver usando o `--label-column-name`, o `--label-column-name` será aquele sendo usado.

Esse argumento é usado apenas para a tarefa de ML supervisionada, tal como um *problema de classificação*. Ele não pode ser usado para tarefas de ML sem supervisão, tais como *clustering*.

----------------------------------------------------------

`--ignore-columns | -I` (string)

Com este argumento, você pode ignorar as colunas existentes no arquivo de conjunto de dados para que elas não sejam carregadas e usadas pelos processos de treinamento.

Especifique os nomes de colunas que você deseja ignorar. Use ',' (vírgula com espaço) ou ' ' (espaço) para separar vários nomes de coluna. Você pode usar aspas para nomes de coluna que contêm espaço em branco (por exemplo, "usuário logado").

Exemplo:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (bool)

Especifique se os arquivos de conjunto de dados têm uma linha de cabeçalho.
Os possíveis valores são:

- `true`
- `false`

O valor padrão será `true` se esse argumento não for especificado pelo usuário.

Para usar o argumento `--label-column-name`, você precisa ter um cabeçalho no arquivo de conjunto de dados e `--has-header` definido como `true` (o que ocorre por padrão).

----------------------------------------------------------

`--max-exploration-time | -x` (string)

Por padrão, o tempo máximo de exploração é de 30 minutos.

Esse argumento define o tempo máximo (em segundos) para o processo explorar vários treinadores e configurações. O tempo configurado poderá ser excedido se o tempo fornecido for muito curto (digamos, dois segundos) para uma única iteração. Nesse caso, o tempo real é o tempo necessário para produzir uma configuração de modelo em uma única iteração.

O tempo necessário para iterações pode variar, dependendo do tamanho do conjunto de dados.

----------------------------------------------------------

`--cache | -c` (string)

Se você usar o armazenamento em cache, o conjunto de dados de treinamento inteiro será carregado na memória.

Para conjuntos de dados pequenos e médios, usar o cache pode melhorar drasticamente o desempenho de treinamento, o que significa que o tempo de treinamento pode ser menor do que quando você não usa o cache.

No entanto, para grandes conjuntos de dados, carregar todos os dados na memória pode ter um efeito negativo, pois você poderá ficar com memória insuficiente. Ao treinar com arquivos de conjunto de dados grandes sem usar o cache, o ML.NET transmitirá partes de dados da unidade quando ele precisar carregar mais dados durante o treinamento.

Você pode especificar os seguintes valores:

`on`: Força o cache a ser usado durante o treinamento.
`off`: Força o cache a não ser usado durante o treinamento.
`auto`: Dependendo da heurística de AutoML, o cache será usado ou não. Em geral, conjuntos de dados pequenos/médios usarão o cache e grandes conjuntos de dados não usarão o cache se você usar a escolha `auto`.

Se você não especificar o parâmetro `--cache`, a configuração de cache `auto` será usada por padrão.

----------------------------------------------------------

`--name | -N` (string)

O nome para a solução ou projeto de saída criado. Se nenhum nome for especificado, o nome `sample-{mltask}` será usado.

O arquivo de modelo do ML.NET (arquivo zip) também receberá o mesmo nome.

----------------------------------------------------------

`--output-path | -o` (string)

Local/pasta raiz para colocar a saída gerada. O padrão é o diretório atual.

----------------------------------------------------------

`--verbosity | -V` (string)

Define o nível de detalhamento da saída padrão.

Os valores permitidos são:

- `q[uiet]`
- `m[inimal]` (por padrão)
- `diag[nostic]` (nível de informações de registro em log)

Por padrão, a ferramenta da CLI deve mostrar alguns comentários mínimos (mínimo) quando estiver funcionando, por exemplo, mencionar que ela está funcionando e, se possível, quanto tempo falta ou que percentual do tempo foi concluído.

----------------------------------------------------------

`-h|--help`

Imprime uma ajuda para o comando com uma descrição para o parâmetro de cada comando.

----------------------------------------------------------

## <a name="see-also"></a>Consulte também

- [Como instalar a ferramenta de CLI do ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Automatizar o treinamento de modelos com a CLI do ML.NET](../automate-training-with-cli.md)
- [Tutorial: Geração automática de um classificador binário usando a CLI do ML.NET](../tutorials/mlnet-cli.md)
- [Telemetria na CLI do ML.NET](../resources/ml-net-cli-telemetry.md)
