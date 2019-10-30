---
title: Operador stackalloc – referência do C#
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 82fc1649bac66c0e934db13c50390b977432c34c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036138"
---
# <a name="stackalloc-operator-c-reference"></a>Operador stackalloc (referência do C#)

O operador `stackalloc` aloca um bloco de memória na pilha. Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado. Não é possível liberar explicitamente a memória alocada com o operador `stackalloc`. Um bloco de memória alocado de pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [instrução`fixed`](../keywords/fixed-statement.md).

Na expressão `stackalloc T[E]`, `T` deve ser um [tipo não gerenciado](../builtin-types/unmanaged-types.md) e `E` deve ser uma expressão do tipo `int`.

Você pode atribuir o resultado do operador `stackalloc` a uma variável de um dos seguintes tipos:

- A partir C# do 7,2, <xref:System.Span%601?displayProperty=nameWithType>ou<xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como mostra o exemplo a seguir:

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  A partir C# do 8,0, você pode usar uma`stackalloc`expressão dentro de outras expressões sempre que uma variável<xref:System.Span%601>ou<xref:System.ReadOnlySpan%601>é permitida, como mostra o exemplo a seguir:

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.

- Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.

  No caso de tipos de ponteiro, você pode usar uma `stackalloc` expressão somente em uma declaração de variável local para inicializar a variável.

O conteúdo da memória recém-alocada é indefinido. A partir C# do 7,3, você pode usar a sintaxe do inicializador de matriz para definir o conteúdo da memória alocada recentemente. O seguinte exemplo demonstra várias maneiras de fazer isso:

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a>Segurança

O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime). Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Alocação de pilha](~/_csharplang/spec/unsafe-code.md#stack-allocation) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores relacionados a ponteiro](pointer-related-operators.md)
- [Tipos de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relativos a memória e extensão](../../../standard/memory-and-spans/index.md)
