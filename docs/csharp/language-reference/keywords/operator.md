---
title: Palavra-chave operator (referência em C#)
description: Saiba como sobrecarregar um operador interno de C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47209366"
---
# <a name="operator-c-reference"></a>operator (Referência de C#)

Use a palavra-chave `operator` para sobrecarregar um operador interno ou para fornecer uma conversão definida pelo usuário em uma declaração de classe ou struct.

Para sobrecarregar um operador em uma classe ou struct personalizada, você pode criar uma declaração do operador no tipo correspondente. A declaração do operador que sobrecarrega um operador interno de C# deve satisfazer as regras a seguir:

- Ela inclui os modificadores `public` e `static`.
- Ela inclui `operator X` em que `X` é o nome ou símbolo do operador que está sendo sobrecarregado.
- Operadores unários têm um parâmetro e operadores binários têm dois parâmetros. Em cada caso, pelo menos um parâmetro deve ser do mesmo tipo que a classe ou struct que declara o operador.

Para obter informações sobre como definir operadores de conversão, consulte os artigos das palavras-chave [explícitas](explicit.md) e [implícitas](implicit.md).

Para uma visão geral de operadores em C# que podem ser sobrecarregados, consulte o artigo [Operadores sobrecarregáveis](../../programming-guide/statements-expressions-operators/overloadable-operators.md).

## <a name="example"></a>Exemplo

O exemplo a seguir define um tipo `Fraction` que representa números fracionários. Ela sobrecarrega os operadores `+` e `*` para executar multiplicação e adição fracionária e também fornece um operador de conversão que converte um tipo `Fraction` em um tipo `double`.

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [implicit](implicit.md)
- [explicit](explicit.md)
- [Operadores sobrecarregáveis](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Como implementar conversões definidas pelo usuário entre structs](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
