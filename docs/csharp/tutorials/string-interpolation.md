---
title: Interpolação de cadeias de caracteres em C#
description: Saiba como incluir resultados de expressão formatada em uma cadeia de caracteres de resultado em C# com a interpolação de cadeia de caracteres.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 5a637937de2f3cff7f5425f47c223a56efa8d0c2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976051"
---
# <a name="string-interpolation-in-c"></a>Interpolação de cadeias de caracteres em C\#

Este tutorial mostra como usar a [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) para formatar e incluir resultados de expressão em uma cadeia de caracteres de resultado. Os exemplos pressupõem que você esteja familiarizado com os conceitos básicos do C# e a formatação de tipos do .NET. Se você não estiver familiarizado com a interpolação de cadeia de caracteres ou com a formatação de tipos do .NET, confira primeiro o [tutorial interativo sobre a interpolação de cadeia de caracteres](../tutorials/intro-to-csharp/interpolated-strings.yml). Para obter mais informações sobre como formatar tipos no .NET, confira o tópico [Formatando tipos no .NET](../../standard/base-types/formatting-types.md).

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Introdução

O recurso [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) baseia-se no recurso [formatação composta](../../standard/base-types/composite-formatting.md) e fornece uma sintaxe mais legível e conveniente para incluir resultados de expressão formatada em uma cadeia de caracteres de resultado.

Para identificar uma literal de cadeia de caracteres como uma cadeia de caracteres interpolada, preceda-o com o símbolo `$`. Você pode inserir qualquer expressão C# válida que retorna um valor em uma cadeia de caracteres interpolada. No seguinte exemplo, assim que uma expressão é avaliada, o resultado é convertido em uma cadeia de caracteres e incluído em uma cadeia de caracteres de resultado:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Como mostra o exemplo, você inclui uma expressão em uma cadeia de caracteres interpolada colocando-a com chaves:

```
{<interpolatedExpression>}
```

No tempo de compilação, normalmente uma cadeia de caracteres interpolada é transformada em uma chamada de método <xref:System.String.Format%2A?displayProperty=nameWithType>. Isso disponibiliza todas as funcionalidades do recurso [formatação composta de cadeia de caracteres](../../standard/base-types/composite-formatting.md) para uso com cadeias de caracteres interpoladas também.

O compilador poderá substituir um <xref:System.String.Format%2A?displayProperty=nameWithType> por <xref:System.String.Concat%2A?displayProperty=nameWithType> se o comportamento analisado for equivalente à concatenação.

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>Como especificar uma cadeia de caracteres de formato para uma expressão interpolada

Especifique uma cadeia de caracteres de formato compatível com o tipo do resultado de expressão seguindo a expressão interpolada com dois-pontos (":") e a cadeia de caracteres de formato:

```
{<interpolatedExpression>:<formatString>}
```

O seguinte exemplo mostra como especificar cadeias de caracteres de formato padrão e personalizadas para expressões que produzem resultados numéricos ou de data e hora:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Para obter mais informações, consulte a seção [Componente de cadeia de caracteres de formato](../../standard/base-types/composite-formatting.md#format-string-component) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md). Esta seção fornece links para tópicos que descrevem cadeias de caracteres de formatos padrão e personalizado compatíveis com os tipos base do .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>Como controlar a largura do campo e o alinhamento da expressão interpolada formatada

Especifique a largura mínima do campo e o alinhamento do resultado de expressão formatada seguindo a expressão interpolada com uma vírgula (",") e a expressão de constante:

```
{<interpolatedExpression>,<alignment>}
```

Se o valor *alignment* for positivo, o resultado da expressão formatada será alinhado à direita; se for negativo, ele será alinhado à esquerda.

Caso precise especificar o alinhamento e uma cadeia de caracteres de formato, comece com o componente de alinhamento:

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

O seguinte exemplo mostra como especificar o alinhamento e usa caracteres de barra vertical ("|") para delimitar campos de texto:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Como mostra a saída de exemplo, se o tamanho do resultado da expressão formatada exceder a largura de campo especificada, o valor *alignment* será ignorado.

Para obter mais informações, consulte a seção [Componente de alinhamento](../../standard/base-types/composite-formatting.md#alignment-component) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md).

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Como usar sequências de escape em uma cadeia de caracteres interpolada

Cadeias de caracteres interpoladas dão suporte a todas as sequências de escape que podem ser usadas em literais de cadeia de caracteres comuns. Para obter mais informações, consulte [Sequências de escape de cadeia de caracteres](../programming-guide/strings/index.md#string-escape-sequences).

Para interpretar sequências de escape literalmente, use um literal de cadeia de caracteres [textual](../language-reference/tokens/verbatim.md). Uma cadeia de caracteres interpolada textual começa com o caractere `$` seguido pelo caractere `@`.

Para incluir uma chave, "{" ou "}", em uma cadeia de caracteres de resultado, use duas chaves, "{{" ou "}}". Para obter mais informações, consulte a seção [Chaves de escape](../../standard/base-types/composite-formatting.md#escaping-braces) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md).

O seguinte exemplo mostra como incluir chaves em uma cadeia de caracteres de resultado e construir uma cadeia de caracteres interpolada textual:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>Como usar um operador condicional ternário `?:` em uma expressão interpolada

Como os dois-pontos (:) têm um significado especial em um item com uma expressão interpolada, para usar um [operador condicional](../language-reference/operators/conditional-operator.md) em uma expressão, coloque-a entre parênteses, como mostra o seguinte exemplo:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Como criar uma cadeia de caracteres de resultado específica a uma cultura com a interpolação de cadeia de caracteres

Por padrão, uma cadeia de caracteres interpolada usa a cultura atual definida pela propriedade <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> para todas as operações de formatação. Use uma conversão implícita de uma cadeia de caracteres interpolada em uma instância <xref:System.FormattableString?displayProperty=nameWithType> e chame seu método <xref:System.FormattableString.ToString(System.IFormatProvider)> para criar uma cadeia de caracteres de resultado específica a uma cultura. O seguinte exemplo mostra como fazer isso:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Como mostra o exemplo, você pode usar uma instância <xref:System.FormattableString> para gerar várias cadeias de caracteres de resultado para várias culturas.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Como criar uma cadeia de caracteres de resultado usando a cultura invariável

Juntamente com o método <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>, você pode usar o método <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> estático para resolver uma cadeia de caracteres interpolada em uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>. O seguinte exemplo mostra como fazer isso:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Conclusão

Este tutorial descreve cenários comuns de uso da interpolação de cadeia de caracteres. Para obter mais informações sobre a interpolação de cadeia de caracteres, consulte o tópico [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md). Para obter mais informações sobre como formatar tipos no .NET, confira os tópicos [Formatando tipos no .NET](../../standard/base-types/formatting-types.md) e [Formatação composta](../../standard/base-types/composite-formatting.md).

## <a name="see-also"></a>Consulte também

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Cadeias de Caracteres](../programming-guide/strings/index.md)
