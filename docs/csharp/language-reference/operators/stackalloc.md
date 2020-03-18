---
title: Operador stackalloc – referência do C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846241"
---
# <a name="stackalloc-operator-c-reference"></a>Operador stackalloc (referência do C#)

O operador `stackalloc` aloca um bloco de memória na pilha. Um bloco de memória alocado na pilha criado durante a execução do método é descartado automaticamente quando esse método é retornado. Não é possível liberar explicitamente a memória alocada com o operador `stackalloc`. Um bloco de memória alocado em pilha não está sujeito à [coleta de lixo](../../../standard/garbage-collection/index.md) e não precisa ser fixado com uma [ `fixed` declaração](../keywords/fixed-statement.md).

Você pode atribuir o resultado do operador `stackalloc` a uma variável de um dos seguintes tipos:

- Começando com C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> ou <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, como o exemplo a seguir mostra:

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  Você não precisa usar um contexto [unsafe](../keywords/unsafe.md) quando atribui um bloco de memória alocado na pilha a uma variável <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.

  Ao trabalhar com esses tipos, você pode usar uma expressão `stackalloc` em [condicional](conditional-operator.md) ou expressões de atribuição, como mostra o seguinte exemplo:

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  Começando com C# 8.0, `stackalloc` você pode usar uma <xref:System.Span%601> <xref:System.ReadOnlySpan%601> expressão dentro de outras expressões sempre que uma ou variável for permitida, como mostra o exemplo a seguir:

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > É recomendável usar os tipos <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> sempre que possível para trabalhar com memória alocada na pilha.

- Um [tipo de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md), como mostra o seguinte exemplo:

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  Como mostra o exemplo anterior, você precisa usar um contexto `unsafe` ao trabalhar com tipos de ponteiro.

  No caso de tipos de ponteiros, você pode usar uma `stackalloc` expressão apenas em uma declaração de variável local para inicializar a variável.

O conteúdo da memória recém-alocada é indefinido. Começando com C# 7.3, você pode usar a sintaxe inicializadora de matriz para definir o conteúdo da memória recém-alocada. O seguinte exemplo demonstra várias maneiras de fazer isso:

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

Na `stackalloc T[E]`expressão, `T` deve ser um `E` tipo não [gerenciado](../builtin-types/unmanaged-types.md) e deve ser uma expressão de tipo [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Segurança

O uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime). Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [de alocação Stack](~/_csharplang/spec/unsafe-code.md#stack-allocation) da especificação do [idioma C#](~/_csharplang/spec/introduction.md) e a Nota de recurso [ `stackalloc` Permitir em contextos aninhados.](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Operadores relacionados a ponteiro](pointer-related-operators.md)
- [Tipos de Ponteiro](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Tipos relacionados a memória e extensão](../../../standard/memory-and-spans/index.md)
