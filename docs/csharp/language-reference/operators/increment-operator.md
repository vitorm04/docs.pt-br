---
title: Operador ++ (Referência de C#)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030457"
---
# <a name="-operator-c-reference"></a>Operador ++ (Referência de C#)

O operador de incremento unário `++` incrementa seu operando em 1. Há duas formas de suporte: o operador de incremento pós-fixado, `x++`, e o operador de incremento de prefixo, `++x`.

## <a name="postfix-increment-operator"></a>Operador de incremento pós-fixado

O resultado de `x++` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a>Operador de incremento de prefixo

O resultado de `++x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a>Comentários

O operador de incremento é predefinido para todos os [tipos integrais](../keywords/integral-types-table.md) (incluindo o tipo [char](../keywords/char.md)), [tipos de ponto flutuante](../keywords/floating-point-types-table.md) e qualquer tipo [enum](../keywords/enum.md).

O operando do operador de incremento deve ser uma variável, um acesso à [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso ao [indexador](../../../csharp/programming-guide/indexers/index.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `++`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira as seções [Operadores de incremento e de decremento pré-fixados](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) e [Operadores de incremento e decremento de prefixo](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) da [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operador --](decrement-operator.md)
- [Como incrementar e diminuir ponteiros](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
