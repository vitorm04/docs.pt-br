---
title: '* Operador – referência do C#'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977338"
---
# <a name="-operator-c-reference"></a>Operador * (referência do C#)

O operador `*` é compatível em duas formas: um operador de indireção de ponteiro unário ou um operador de multiplicação binário.

## <a name="pointer-indirection-operator"></a>Operador de indireção de ponteiro

Use o operador `*` unário para obter a variável para a qual aponta o operando de um tipo de ponteiro. Veja mais informações em [Como obter o valor de uma variável de ponteiro](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).

O operador de indireção de ponteiro `*` requer o contexto [não seguro](../keywords/unsafe.md).

## <a name="multiplication-operator"></a>Operador de multiplicação

Para tipos numéricos, o operador `*` calcula o produto dos operandos:

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) um operador `*` binário. Quando um operador `*` binário é sobrecarregado, o [operador de atribuição de multiplicação](multiplication-assignment-operator.md) `*=` também é implicitamente sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Veja mais informações, nas seções [Indireção de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-indirection) e [Operador de multiplicação](~/_csharplang/spec/expressions.md#multiplication-operator) da [ especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)