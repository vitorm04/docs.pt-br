---
title: Operador padrão – Referência do C#
description: Use o operador padrão para produzir o valor padrão de um tipo
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399479"
---
# <a name="default-operator-c-reference"></a>operador padrão (referência do C#)

O operador `default` produz o [valor padrão](../builtin-types/default-values.md) de um tipo. O argumento para o operador `default` deve ser o nome ou um parâmetro de tipo.

O exemplo a seguir mostra o uso do operador `default`:

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

Você também `default` usa a palavra-chave como o rótulo de caso padrão dentro de uma [ `switch` declaração](../keywords/switch.md).

## <a name="default-literal"></a>literal padrão

A partir do C# 7,1, você pode usar o literal `default` para produzir o valor padrão de um tipo quando o compilador pode inferir o tipo de expressão. A expressão literal `default` produz o mesmo valor que a expressão `default(T)`, em que `T` é o tipo inferido. Você pode usar o literal `default` em qualquer um dos seguintes casos:

- Na atribuição ou inicialização de uma variável.
- Na declaração do valor padrão para um [parâmetro de método opcional.](../../methods.md#optional-parameters-and-arguments)
- Em uma chamada de método para fornecer um valor de argumento.
- Em uma [ `return` declaração](../keywords/return.md) ou como uma expressão em um [membro encorpado de expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

O exemplo a seguir mostra o uso do literal `default`:

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Expressões de valor padrão](~/_csharplang/spec/expressions.md#default-value-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

Para obter mais informações sobre o literal `default`, confira a [nota da proposta do recurso](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Valores padrão dos tipos C#](../builtin-types/default-values.md)
- [Genéricos no .NET](../../../standard/generics/index.md)
