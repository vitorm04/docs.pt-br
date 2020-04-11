---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: 'Conheça os tipos de ponto flutuante C# embutidos: flutuar, dobrar e decimal'
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121477"
---
# <a name="floating-point-numeric-types-c-reference"></a>Tipos numéricos de ponto flutuante (Referência de C#)

Os *tipos numéricos de ponto flutuante* representam números reais. Todos os tipos numéricos de ponto flutuante são tipos de [valor](value-types.md). Eles também são [tipos simples](value-types.md#built-in-value-types) e podem ser inicializados com [literais](#real-literals). Todos os tipos numéricos de ponto flutuante suportam [operadores aritméticos,](../operators/arithmetic-operators.md) [de comparação](../operators/comparison-operators.md)e [de igualdade.](../operators/equality-operators.md)

## <a name="characteristics-of-the-floating-point-types"></a>Características dos tipos de ponto flutuante

O C# é compatível com os seguintes tipos de pontos flutuantes predefinidos:
  
|palavra-chave/tipo C#|Intervalo aproximado|Precisão|Tamanho|Tipo .NET|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup>|~6 a 9 dígitos|4 bytes|<xref:System.Single?displayProperty=nameWithType>|
|`double`|±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup>|~15 a 17 dígitos|8 bytes|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup>|28 a 29 dígitos|16 bytes|<xref:System.Decimal?displayProperty=nameWithType>|

Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente. Eles são intercambiáveis. Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:

```csharp
double a = 12.3;
System.Double b = 12.3;
```

O valor padrão de cada tipo de ponto flutuante é zero, `0`. Cada um dos tipos de ponto flutuante possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo. Os tipos `float` e `double` também fornecem constantes que representam valores não numéricos e infinitos. Por exemplo, o tipo `double` fornece as seguintes constantes: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> e <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.

Como o tipo `decimal` tem mais precisão e um intervalo menor que `float` e `double`, ele é apropriado para cálculos financeiros e monetários.

Você pode misturar tipos `float` `double` [integrais](integral-numeric-types.md) e os tipos em uma expressão. Neste caso, os tipos integrais são implicitamente convertidos em um `float` dos tipos de ponto `double`flutuante e, se necessário, o tipo é implicitamente convertido para . A expressão é avaliada como segue:

- Se houver `double` tipo na expressão, a `double`expressão avalia [`bool`](bool.md) , ou em comparações relacionais e de igualdade.
- Se não `double` houver nenhum tipo na expressão, `float`a `bool` expressão avalia , ou em comparações relacionais e de igualdade.

Você também pode misturar `decimal` tipos integrais e o tipo em uma expressão. Neste caso, os tipos integrais são `decimal` implicitamente convertidos `decimal`ao `bool` tipo e a expressão avalia , ou para em comparações relacionais e de igualdade.

Você não `decimal` pode misturar `float` `double` o tipo com os tipos e em uma expressão. Neste caso, se você quiser realizar operações de aritmética, comparação ou igualdade, você deve converter `decimal` explicitamente os operands de ou para o tipo, como o exemplo a seguir mostra:

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.

## <a name="real-literals"></a>Literais reais

O tipo de literal real é determinado pelo seu sufixo da seguinte forma:

- O literal sem sufixo ou com o `d` ou `D` sufixo é do tipo`double`
- O literal `f` com `F` o ou sufixo é do tipo`float`
- O literal `m` com `M` o ou sufixo é do tipo`decimal`

O código a seguir demonstra um exemplo de cada um:

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

O exemplo anterior também `_` mostra o uso de como *separador de dígitos,* que é suportado a partir de C# 7.0. Você pode usar o separador de dígitos com todos os tipos de literais numéricos.

Você também pode usar a notação científica, ou seja, especificar uma parte expoente de um literal real, como o exemplo a seguir mostra:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Conversões

Há apenas uma conversão implícita entre os tipos `float` numéricos de ponto flutuante: de . `double` No entanto, você pode converter qualquer tipo de ponto flutuante para qualquer outro tipo de ponto flutuante com o [gesso explícito](../operators/type-testing-and-cast.md#cast-expression). Para obter mais informações, consulte [conversões numéricas incorporadas](numeric-conversions.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos de pontos flutuantes](~/_csharplang/spec/types.md#floating-point-types)
- [O tipo decimal](~/_csharplang/spec/types.md#the-decimal-type)
- [Literais reais](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de valor](value-types.md)
- [Tipos integrais](integral-numeric-types.md)
- [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md)
- [Numéricos no .NET](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
