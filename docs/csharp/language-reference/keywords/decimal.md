---
title: Palavra-chave decimal (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 18924abefb85012fc6c61073603c594de906b58d
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027948"
---
# <a name="decimal-c-reference"></a>decimal (Referência de C#)

A palavra-chave `decimal` indica um tipo de dados de 128 bits. Comparado a outros tipos de pontos flutuantes, o tipo `decimal` tem mais precisão e um intervalo menor que o torna apropriado para cálculos financeiros e monetários. O intervalo e a precisão aproximados para o tipo `decimal` são mostrados na tabela a seguir.

|Tipo|Intervalo aproximado|Precisão|Tipo .NET|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|(-7,9 x 10<sup>28</sup> a 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> a 10<sup>28</sup>)|28 a 29 dígitos significativos|<xref:System.Decimal?displayProperty=nameWithType>|

O valor padrão de um `decimal` é 0m.

## <a name="literals"></a>Literais

Se você desejar tratar um literal numérico como `decimal`, use o sufixo m ou M, por exemplo:

```csharp
decimal myMoney = 300.5m;
```

Sem o sufixo m, o número será tratado como [double](../../../csharp/language-reference/keywords/double.md) e gerará um erro do compilador.

## <a name="conversions"></a>Conversões

Os tipos integrais são convertidos implicitamente em `decimal` e o resultado é avaliado como `decimal`. Portanto, você pode inicializar uma variável decimal com um literal inteiro sem o sufixo como a seguir:

```csharp
decimal myMoney = 300;
```

Não há nenhuma conversão implícita entre outros tipos de pontos flutuantes e o tipo `decimal`. Portanto, uma conversão deve ser usada para converter entre esses dois tipos. Por exemplo:

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

Você também pode misturar `decimal` e tipos integrais numéricos na mesma expressão. No entanto, misturar `decimal` e outros tipos de pontos flutuantes sem uma conversão causa um erro de compilação.

Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).

Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).

## <a name="formatting-decimal-output"></a>Formatar a saída decimal

Você pode formatar os resultados ao usar o método `String.Format` ou <xref:System.Console.Write%2A?displayProperty=nameWithType> que chama `String.Format()`. O formato de moeda é especificado ao usar a cadeia de caracteres de formato de moeda padrão "C" ou "c", como mostrado no segundo exemplo posteriormente neste artigo. Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo a seguir causa um erro do compilador ao tentar adicionar variáveis [double](../../../csharp/language-reference/keywords/double.md) e `decimal`.

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

O resultado é o seguinte erro:

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

Neste exemplo, um `decimal` e um [int](../../../csharp/language-reference/keywords/int.md) são misturados na mesma expressão. O resultado é avaliado como o tipo `decimal`.

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>Exemplo

Neste exemplo, a saída é formatada usando a cadeia de caracteres de formato de moeda. Observe que `x` é arredondado porque as casas decimais excedem US$ 0,99. A variável `y`, que representa os dígitos exatos máximos, é exibida exatamente no formato correto.

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

<xref:System.Decimal>  
[Referência de C#](../../../csharp/language-reference/index.md)  
[Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
[Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
[Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
[Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
[Cadeias de Caracteres de Formato Numérico Padrão](../../../standard/base-types/standard-numeric-format-strings.md)