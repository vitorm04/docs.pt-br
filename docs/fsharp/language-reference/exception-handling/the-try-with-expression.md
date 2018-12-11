---
title: 'Exceções: A instrução try... with expressão (F#)'
description: Saiba como usar o F# 'try... com' expressão para manipulação de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 946cf56f7abc4bd5e3a9f9acc52b868bd6c7f84a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127401"
---
# <a name="exceptions-the-trywith-expression"></a>Exceções: A expressão try...with

Este tópico descreve o `try...with` expressão, a expressão que é usada para manipulação de exceção no F# idioma.

## <a name="syntax"></a>Sintaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Comentários

O `try...with` expressão é usada para manipular exceções em F#. Ele é semelhante ao `try...catch` instrução em c#. Na sintaxe anterior, o código na *expression1* pode gerar uma exceção. O `try...with` expressão retorna um valor. Se nenhuma exceção for lançada, toda a expressão retorna o valor da *expression1*. Se uma exceção for lançada, cada *padrão* são comparados por sua vez, com a exceção e para o primeiro padrão de correspondência, correspondente *expressão*, conhecido como o *domanipuladordeexceção*, para essa ramificação é executada, e a expressão geral retorna o valor da expressão nesse manipulador de exceção. Se nenhum padrão corresponder, a exceção for propagada até a pilha de chamada até que um manipulador correspondente for encontrado. Os tipos dos valores retornados de cada expressão nos manipuladores de exceção devem corresponder ao tipo retornado da expressão no `try` bloco.

Com frequência, o fato de que ocorreu um erro também significa que não há nenhum valor válido que pode ser retornado de expressões em cada manipulador de exceção. Um padrão frequente deve ter o tipo da expressão a ser um tipo de opção. O exemplo de código a seguir ilustra esse padrão.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

As exceções podem ser exceções .NET, ou podem ser F# exceções. Você pode definir F# exceções usando o `exception` palavra-chave.

Você pode usar uma variedade de padrões para filtrar o tipo de exceção e outras condições; as opções são resumidas na tabela a seguir.

|Padrão|Descrição|
|-------|-----------|
|:? *tipo de exceção*|Corresponde ao tipo de exceção .NET especificado.|
|:? *tipo de exceção* como *identificador*|Corresponde ao tipo de exceção .NET especificado, mas oferece a exceção de um valor nomeado.|
|*nome da exceção*(*argumentos*)|Correspondências de um F# tipo de exceção e associa os argumentos.|
|*identifier*|Corresponde a qualquer exceção e associa o nome para o objeto de exceção. Equivalente a **:? System. Exception como**_identificador_|
|*identificador* quando *condição*|Corresponde a qualquer exceção se a condição for verdadeira.|

## <a name="examples"></a>Exemplos

Os exemplos de código a seguir ilustram o uso de vários padrões de manipulador de exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> O `try...with` construção é uma expressão separada do `try...finally` expressão. Portanto, se seu código requer tanto uma `with` bloco e um `finally` bloco, será necessário aninhar as duas expressões.

> [!NOTE]
> Você pode usar `try...with` nos fluxos de trabalho assíncronos e outras expressões de computação, nesse caso, uma versão personalizada do `try...with` expressão é usada. Para obter mais informações, consulte [fluxos de trabalho assíncronos](../asynchronous-workflows.md), e [expressões de computação](../computation-expressions.md).

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: O `try...finally` expressão](the-try-finally-expression.md)
