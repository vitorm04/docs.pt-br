---
title: stackalloc (Referência de C#)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 5926550eea1f5a2f8fb74645f22ca54c2bed3136
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508574"
---
# <a name="stackalloc-c-reference"></a>stackalloc (Referência de C#)
A palavra-chave `stackalloc` é usada em um contexto de código não seguro para alocar um bloco de memória na pilha.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Comentários

A palavra-chave é válida somente em inicializadores de variável locais. O código a seguir gera erros de compilador.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

A partir do C# 7.3, é possível usar a sintaxe do inicializador de matriz para matrizes de `stackalloc`. Todas as declarações a seguir declaram uma matriz com três elementos cujos valores são os inteiros `1`, `2` e `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

Como tipos de ponteiro estão envolvidos, `stackalloc` requer o contexto [não seguro](unsafe.md). Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` é como [_alloca](/cpp/c-runtime-library/reference/alloca) na biblioteca de tempo de execução C.

## <a name="examples"></a>Exemplos

O exemplo a seguir calcula e exibe os 20 primeiros números na sequência de Fibonacci. Cada número é a soma dos dois números anteriores. No código, um bloco de memória de tamanho suficiente para conter 20 elementos do tipo `int` é alocado na pilha, não no heap. O endereço do bloco é armazenado no ponteiro `fib`. Essa memória não está sujeita à coleta de lixo e, portanto, não precisa ser fixado (usando [fixed](fixed-statement.md)). O tempo de vida do bloco de memória é limitado ao tempo de vida do método que o define. Você não pode liberar a memória antes de o método retornar.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

O exemplo a seguir inicializa uma matriz `stackalloc` de inteiros em uma máscara de bits com um bit definido em cada elemento. Isso demonstra a nova sintaxe do inicializador disponível a partir do C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Segurança

O código não seguro é menos seguro do que as alternativas seguras. No entanto, o uso de `stackalloc` habilita automaticamente os recursos de detecção de estouro de buffer no CLR (Common Language Runtime). Se for detectada uma estouro de buffer, o processo será encerrado assim que possível para minimizar a chance de o código mal-intencionado ser executado.

## <a name="c-language-specification"></a>Especificação da Linguagem C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
