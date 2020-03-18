---
title: $ - interpolação de cordas - Referência C#
description: A interpolação de cadeia de caracteres oferece uma sintaxe mais legível e conveniente para formatar a saída de cadeia de caracteres de formatação do que a tradicional formatação composta da cadeia de caracteres.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980113"
---
# <a name="---string-interpolation-c-reference"></a>$ - interpolação de cordas (referência C#)

O caractere especial `$` identifica um literal de cadeia de caracteres como uma *cadeia de caracteres interpolada*. Uma cadeia de caracteres interpolada é um literal de cadeia de caracteres que pode conter *expressões de interpolação*. Quando uma cadeia de caracteres interpolada é resolvida em uma cadeia de caracteres de resultado, itens com expressões de interpolação são substituídos pelas representações de cadeia de caracteres dos resultados da expressão. Este recurso está disponível a partir de C# 6.

A interpolação de cadeia de caracteres fornece uma sintaxe mais legível e conveniente para criar cadeias de caracteres formatadas do que o recurso de [formatação composta de cadeia de caracteres](../../../standard/base-types/composite-formatting.md). O exemplo a seguir usa os dois recursos para produzir o mesmo resultado:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Estrutura de uma cadeia de caracteres interpolada

Para identificar uma literal de cadeia de caracteres como uma cadeia de caracteres interpolada, preceda-o com o símbolo `$`. Não pode haver nenhum espaço em branco entre o `$` e `"` que iniciam um literal de cadeia de caracteres.

A estrutura de um item com uma expressão de interpolação é da seguinte maneira:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Os elementos entre colchetes são opcionais. A seguinte tabela descreve cada elemento:

|Elemento|Descrição|
|-------------|-----------------|
|`interpolationExpression`|A expressão que produz um resultado a ser formatado. Representação `null` de <xref:System.String.Empty?displayProperty=nameWithType>cordas de é .|
|`alignment`|A expressão constante cujo valor define o número mínimo de caracteres na representação de seqüência do resultado da expressão. Se for positiva, a representação de cadeia de caracteres será alinhada à direita; se for negativa, será alinhada à esquerda. Para obter mais informações, consulte [Componente de alinhamento](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Uma cadeia de caracteres de formato compatível com o tipo do resultado da expressão. Para obter mais informações, consulte [Componente da cadeia de caracteres de formato](../../../standard/base-types/composite-formatting.md#format-string-component).|

O exemplo a seguir usa os componentes opcionais de formatação descritos acima:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Caracteres especiais

Para incluir uma chave, "{" ou "}", no texto produzido por uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}". Para obter mais informações, consulte [Chaves de escape](../../../standard/base-types/composite-formatting.md#escaping-braces).

Como os dois-pontos (":") têm um significado especial em um item de expressão de interpolação, para usar um [operador condicional](../operators/conditional-operator.md) em uma expressão de interpolação, coloque essa expressão entre parênteses.

O seguinte exemplo mostra como incluir uma chave em uma cadeia de caracteres de resultado e como usar um operador condicional em uma expressão de interpolação:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Uma seqüência de caracteres `$` interpolada `@` começa com o personagem seguido pelo personagem. Para obter mais informações sobre cadeias de caracteres textuais, confira os tópicos [cadeia de caracteres](../builtin-types/reference-types.md) e [identificador textual](verbatim.md).

> [!NOTE]
> Começando com C# 8.0, `$` você `@` pode usar os tokens em qualquer ordem: ambos `$@"..."` e `@$"..."` são cadeias verbatim interpoladas válidas. Nas versões C# anteriores, `$` `@` o token deve aparecer antes do token.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Conversões implícitas e `IFormatProvider` como especificar a implementação

Há três conversões implícitas de uma cadeia de caracteres interpolada:

1. Conversão de uma cadeia de caracteres interpolada uma instância <xref:System.String>, que é a resolução da cadeia de caracteres interpolada com os itens da expressão de interpolação que estão sendo substituídos pelas representações de seus resultados da cadeia de caracteres corretamente formatada. Esta conversão <xref:System.Globalization.CultureInfo.CurrentCulture> usa os resultados de expressão para formatar.

1. Conversão de uma cadeia de caracteres interpolada em uma instância de <xref:System.FormattableString>, que representa uma cadeia de caracteres de formato composto, juntamente com os resultados da expressão a ser formatada. Isso permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.FormattableString>. Para fazer isso, ligue para um dos seguintes métodos:

      - Uma sobrecarga <xref:System.FormattableString.ToString> que produza uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Um método <xref:System.FormattableString.Invariant%2A> que produz uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - Um método <xref:System.FormattableString.ToString(System.IFormatProvider)> que produza uma cadeia de caracteres de resultado para uma cultura específica.

    Use também o método <xref:System.FormattableString.ToString(System.IFormatProvider)> para fornecer uma implementação definida pelo usuário da interface <xref:System.IFormatProvider> que dá suporte à formatação personalizada. Para obter mais informações, consulte a formatação personalizada com a seção [ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) dos tipos de formatação no artigo [.NET.](../../../standard/base-types/formatting-types.md)

1. Conversão de uma cadeia de caracteres interpolada em uma instância <xref:System.IFormattable>, que também permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.IFormattable>.

O exemplo a seguir usa a conversão implícita em <xref:System.FormattableString> para a criação de cadeias de caracteres de resultado específicas de cultura:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Recursos adicionais

Se não estiver familiarizado com a interpolação de cadeia de caracteres, confira o tutorial [Interpolação de cadeia de caracteres no C# Interativo](../../tutorials/exploration/interpolated-strings.yml). Você também pode verificar outro tutorial de [interpolação de cadeia de caracteres C#](../../tutorials/string-interpolation.md) que demonstra como usar cadeias de caracteres interpoladas para produzir cadeias de caracteres formatadas.

## <a name="compilation-of-interpolated-strings"></a>Compilação de cadeias de caracteres interpoladas

Se uma cadeia de caracteres interpolada tiver o tipo `string`, ela normalmente será transformada em uma chamada de método <xref:System.String.Format%2A?displayProperty=nameWithType>. O compilador pode substituir <xref:System.String.Format%2A?displayProperty=nameWithType> por <xref:System.String.Concat%2A?displayProperty=nameWithType> se o comportamento analisado for equivalente à concatenação.

Se uma cadeia de caracteres interpolada tiver o tipo <xref:System.IFormattable> ou <xref:System.FormattableString>, o compilador gerará uma chamada para o método <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [cadeias de caracteres interpoladas](~/_csharplang/spec/expressions.md#interpolated-strings) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Caracteres especiais de C#](index.md)
- [Cadeias de caracteres](../../programming-guide/strings/index.md)
- [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md)
- [Formatação de composição](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
