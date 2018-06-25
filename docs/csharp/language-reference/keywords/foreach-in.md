---
title: foreach, in (Referência de C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 7613590686f7f7ec6439da4a2bb672e524ab01e8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565700"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência de C#)

A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:

- incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,
- o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.

Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md). Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).

## <a name="examples"></a>Exemplos

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

[A instrução foreach (especificação da linguagem C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Usando foreach com matrizes](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Instruções de iteração](iteration-statements.md)  
[Palavras-chave do C#](index.md)  
[Referência de C#](../index.md)  
[Guia de Programação em C#](../../programming-guide/index.md)  