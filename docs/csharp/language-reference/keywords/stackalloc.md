---
title: Palavra-chave stackalloc – Referência de C#
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480801"
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referência de C#)

A palavra-chave `stackalloc` é usada para alocar um bloco de memória na pilha.

```csharp
Span<int> block = stackalloc int[100];
```

Atribuir o bloco alocado a um <xref:System.Span%601?displayName=nameWithType> em vez de um `int*` permite alocações de pilha em um bloco seguro. O contexto `unsafe` não é obrigatório.

## <a name="remarks"></a>Comentários

A palavra-chave é válida somente em inicializadores de variável locais. O código a seguir gera erros de compilador.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

A partir do C# 7.3, é possível usar a sintaxe do inicializador de matriz para matrizes de `stackalloc`. Todas as declarações a seguir declaram uma matriz com três elementos cujos valores são os inteiros `1`, `2` e `3`. A segunda inicialização atribui a memória a um <xref:System.ReadOnlySpan%601>, indicando que a memória não pode ser modificada.

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

Quando tipos de ponteiro estão envolvidos, `stackalloc` requer um contexto [não seguro](unsafe.md). Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).

`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.

## <a name="examples"></a>Exemplos

O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci. Cada número é a soma dos dois números anteriores. No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap. O endereço do bloco é armazenado no `Span` `fib`. Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](fixed-statement.md)). O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define. Você não pode liberar a memória antes de o método retornar.

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

O exemplo a seguir inicializa uma matriz `stackalloc` de inteiros em uma máscara de bits com um bit definido em cada elemento. Isso demonstra a nova sintaxe do inicializador disponível a partir do C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Segurança

Você deve usar <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> quando possível porque códigos não gerenciados são menos seguros do que alternativas seguras. Mesmo quando usado com ponteiros, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime). Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Palavras-chave do operador](operator-keywords.md)
- [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md)
