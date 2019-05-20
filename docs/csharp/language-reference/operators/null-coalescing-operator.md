---
title: ?? Operador – referência do C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: e1e981f9ec6a87f6e7de1900008520cde8e46095
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633942"
---
# <a name="-operator-c-reference"></a>?? operator (Referência de C#)

O operador `??` é chamado operador de coalescência nula.  Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.

## <a name="remarks"></a>Comentários

Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo). Você pode usar a expressividade sintática do operador `??` para retornar um valor adequado (o operando direito) quando o operando esquerdo tiver um tipo que permite valor nulo cujo valor seja nulo. Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado. Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.

Para obter mais informações, consulte [Tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md).

O resultado de um operador ?? não será considerado constante, mesmo se os dois argumentos forem constantes.

## <a name="example"></a>Exemplo

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md)
- [O que exatamente “levantado” significa?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
