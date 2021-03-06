---
title: Dividir cadeias de caracteres usando String. Split (guia C#)
description: O método Split retorna uma matriz de cadeias de caracteres divididas de um conjunto de delimitadores. É uma maneira fácil de extrair subsequências de uma cadeia de caracteres.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 5361a3c60905edd19b180c5ddb14064a85f64337
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400494"
---
# <a name="how-to-separate-strings-using-stringsplit-in-c"></a>Como separar cadeias de caracteres usando String. Split em C\#

O método <xref:System.String.Split%2A?displayProperty=nameWithType> cria uma matriz de subcadeias, dividindo a cadeia de caracteres de entrada com base em um ou mais delimitadores. Esse método é geralmente a maneira mais fácil de separar uma cadeia de caracteres em limites de palavras. Ele também é usado para dividir cadeias de caracteres em outras cadeias ou caractere específico.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

O código a seguir divide uma frase comum em uma matriz de cadeias de caracteres para cada palavra.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

Cada instância de um caractere separador produz um valor na matriz retornada. Caracteres separadores consecutivos produzem a cadeia de caracteres vazia como um valor na matriz retornada. Você pode ver como uma cadeia de caracteres vazia é criada no exemplo a seguir, que usa o caractere de espaço como um separador.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

Esse comportamento torna mais fácil para formatos como arquivos de valores separados por vírgulas (CSV) que representam dados tabulares. Vírgulas consecutivas representam uma coluna em branco.

Você pode passar um parâmetro <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> opcional para excluir as cadeias de caracteres vazias da matriz retornada. Para um processamento mais complicado da coleção retornada, você pode usar o [LINQ](../programming-guide/concepts/linq/index.md) para manipular a sequência de resultado.

O <xref:System.String.Split%2A?displayProperty=nameWithType> pode usar vários caracteres separadores.
O exemplo a seguir usa espaços, vírgulas, pontos, dois-pontos e tabulações como separando caracteres, que são passados para <xref:System.String.Split%2A> em uma matriz.
O loop, na parte inferior do código, exibe cada uma das palavras na matriz retornada.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

As instâncias consecutivas de qualquer separador produzem a cadeia de caracteres vazia na matriz de saída:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

O <xref:System.String.Split%2A?displayProperty=nameWithType> pode receber uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>Confira também

- [Extrair elementos de uma cadeia de caracteres](../../standard/base-types/divide-up-strings.md)
- [Guia de programação em C#](../programming-guide/index.md)
- [Cadeias de caracteres](../programming-guide/strings/index.md)
- [Expressões regulares do .NET](../../standard/base-types/regular-expressions.md)
