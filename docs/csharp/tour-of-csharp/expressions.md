---
title: Expressões C# - um tour pela linguagem C#
description: Expressões, operandos e operadores são blocos de compilação da linguagem C#
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4866d12118518827c1f7032ac09933927f0f3c52
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395670"
---
# <a name="expressions"></a>{1&gt;Expressões&lt;1}

*Expressões* são construídas a partir de *operandos* e *operadores*. Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos. Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`. Exemplos de operandos incluem literais, campos, variáveis locais e expressões.

Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados. Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.

Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:

* Exceto para os operadores de atribuição e de União nulo, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita. Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.
* Os operadores de atribuição, a `??` de União nula e os operadores de `??=` e o operador condicional `?:` são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda. Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.

Precedência e associatividade podem ser controladas usando parênteses. Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.

A maioria dos operadores pode ser [*sobrecarregada*](../language-reference/operators/operator-overloading.md). A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.

C# fornece uma série de operadores para realizar operações [aritméticas](../language-reference/operators/arithmetic-operators.md), [lógicas](../language-reference/operators/boolean-logical-operators.md), [bit a bit e shift](../language-reference/operators/bitwise-and-shift-operators.md) e comparações de [igualdade](../language-reference/operators/equality-operators.md) e [ordem](../language-reference/operators/comparison-operators.md).

Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Anterior](types-and-variables.md)
> [Próximo](statements.md)
