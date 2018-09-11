---
title: $ – interpolação de cadeia de caracteres (Referência de C#)
description: A interpolação de cadeia de caracteres oferece uma sintaxe mais legível e conveniente para formatar a saída de cadeia de caracteres de formatação do que a tradicional formatação composta da cadeia de caracteres.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 2009b3620bc4874520221a4ea847222feafca01b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251726"
---
# <a name="---string-interpolation-c-reference"></a>$ – interpolação de cadeia de caracteres (Referência de C#)

O caractere especial `$` identifica um literal de cadeia de caracteres como uma *cadeia de caracteres interpolada*. Uma cadeia de caracteres interpolada é um literal de cadeia de caracteres que pode conter *expressões interpoladas*. Quando uma cadeia de caracteres interpolada é resolvida em uma cadeia de caracteres de resultado, itens com expressões interpoladas são substituídos pelas representações de cadeia de caracteres dos resultados da expressão. Este recurso está disponível no C# 6 e em versões posteriores da linguagem.

A interpolação de cadeia de caracteres fornece uma sintaxe mais legível e conveniente para criar cadeias de caracteres formatadas do que o recurso de [formatação composta de cadeia de caracteres](../../../standard/base-types/composite-formatting.md). O exemplo a seguir usa os dois recursos para produzir o mesmo resultado:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Estrutura de uma cadeia de caracteres interpolada

Para identificar uma literal de cadeia de caracteres como uma cadeia de caracteres interpolada, preceda-a com o símbolo `$`. Não pode haver nenhum espaço em branco entre o `$` e `"` que iniciam um literal de cadeia de caracteres. Fazer isso causa um erro em tempo de compilação.

A estrutura de um item com uma expressão interpolada é da seguinte maneira:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Os elementos entre colchetes são opcionais. A seguinte tabela descreve cada elemento:

|Elemento|Descrição|
|-------------|-----------------|
|`interpolatedExpression`|A expressão que produz um resultado a ser formatado. A representação de cadeia de caracteres do resultado `null` é <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|A expressão de constante cujo valor define o número mínimo de caracteres da representação de cadeia de caracteres do resultado da expressão interpolada. Se for positiva, a representação de cadeia de caracteres será alinhada à direita; se for negativa, será alinhada à esquerda. Para obter mais informações, consulte [Componente de alinhamento](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Uma cadeia de caracteres de formato compatível com o tipo do resultado da expressão. Para obter mais informações, consulte [Componente da cadeia de caracteres de formato](../../../standard/base-types/composite-formatting.md#format-string-component).|

O exemplo a seguir usa os componentes opcionais de formatação descritos acima:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Caracteres especiais

Para incluir uma chave, "{" ou "}", no texto produzido por uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}". Para obter mais informações, consulte [Chaves de escape](../../../standard/base-types/composite-formatting.md#escaping-braces).

Como os dois-pontos (":") têm um significado especial em um item de expressão interpolada, para usar um [operador condicional](../operators/conditional-operator.md) em uma expressão interpolada, coloque essa expressão entre parênteses.

O seguinte exemplo mostra como incluir uma chave em uma cadeia de caracteres de resultado e como usar um operador condicional em uma expressão interpolada:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Uma cadeia de caracteres interpolada textual começa com o caractere `$` seguido pelo caractere `@`. Para obter mais informações sobre cadeias de caracteres textuais, confira os tópicos [cadeia de caracteres](../keywords/string.md) e [identificador textual](verbatim.md).

> [!NOTE]
> O token `$` deve aparecer antes do token `@` em uma cadeia de caracteres textual interpolada.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Conversões implícitas e especificando a implementação de `IFormatProvider`

Há três conversões implícitas de uma cadeia de caracteres interpolada:

1. Conversão de uma cadeia de caracteres interpolada uma instância <xref:System.String>, que é a resolução da cadeia de caracteres interpolada com os itens da expressão interpolada que estão sendo substituídos pelas representações de seus resultados da cadeia de caracteres corretamente formatada. Essa conversão usa a cultura atual.

1. Conversão de uma cadeia de caracteres interpolada em uma instância de <xref:System.FormattableString>, que representa uma cadeia de caracteres de formato composto, juntamente com os resultados da expressão a ser formatada. Isso permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.FormattableString>. Para fazer isso, chame um dos seguintes métodos:

      - Uma sobrecarga <xref:System.FormattableString.ToString> que produza uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Um método <xref:System.FormattableString.Invariant%2A> que produz uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - Um método <xref:System.FormattableString.ToString(System.IFormatProvider)> que produza uma cadeia de caracteres de resultado para uma cultura específica.

    Use também o método <xref:System.FormattableString.ToString(System.IFormatProvider)> para fornecer uma implementação definida pelo usuário da interface <xref:System.IFormatProvider> que dá suporte à formatação personalizada. Para obter mais informações, confira [Formatação personalizada com ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Conversão de uma cadeia de caracteres interpolada em uma instância <xref:System.IFormattable>, que também permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.IFormattable>.

O exemplo a seguir usa a conversão implícita em <xref:System.FormattableString> para a criação de cadeias de caracteres de resultado específicas de cultura:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Recursos adicionais

Se não estiver familiarizado com a interpolação de cadeia de caracteres, confira o guia de início rápido [Interpolação de cadeia de caracteres no C#](../../quick-starts/interpolated-strings.yml). Para obter mais exemplos, confira o tutorial [Interpolação de cadeia de caracteres no C#](../../tutorials/string-interpolation.md).

## <a name="see-also"></a>Consulte também

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Formatação de composição](../../../standard/base-types/composite-formatting.md)
- [Cadeias de Caracteres](../../programming-guide/strings/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Caracteres especiais de C#](index.md)
- [Referência de C#](../index.md)
