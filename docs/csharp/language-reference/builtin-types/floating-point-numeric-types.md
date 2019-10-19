---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: Visão geral sobre os tipos de ponto flutuante internos do C#
ms.date: 10/18/2019
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
ms.openlocfilehash: fa6cbb869d90113414cc6f8ffe231386c3596b1d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579379"
---
# <a name="floating-point-numeric-types-c-reference"></a>Tipos numéricos de ponto flutuante (Referência de C#)

Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#real-literals). Todos os tipos de ponto flutuante também são tipos de valor. Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .

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

É possível misturar tipos [integrais](integral-numeric-types.md) e de ponto flutuante em uma expressão. Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante. A avaliação da expressão é executada de acordo com as regras a seguir:

- Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.
- Se não houver nenhum tipo de `double` na expressão, a expressão será avaliada como `float` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.

Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:

- Zero positivo e negativo
- Infinito positivo e negativo
- Valor NaN (não é um número)
- O conjunto finito de valores diferentes de zero

Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).

É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.

## <a name="real-literals"></a>Literais reais

O tipo de um literal real é determinado pelo seu sufixo da seguinte maneira:

- O literal sem sufixo ou com o sufixo `d` ou `D` é do tipo `double`
- O literal com o sufixo `f` ou `F` é do tipo `float`
- O literal com o sufixo `m` ou `M` é do tipo `decimal`

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

O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0. Você pode usar o separador de dígitos com todos os tipos de literais numéricos.

Você também pode usar a notação científica, ou seja, especificar uma parte exponencial de um literal real, como mostra o exemplo a seguir:

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita (chamada de *conversão de expansão*) de `float` em `double` porque o intervalo dos valores `float` é um subconjunto adequado de `double` e não há perda de precisão de `float` para `double`.

É necessário usar uma conversão explícita para converter um tipo de ponto flutuante em outro quando uma conversão implícita não está definida do tipo de origem para o tipo de destino. Isso é chamado de *conversão de estreitamento*. O caso explícito é necessário porque a conversão pode resultar em perda de dados. Não há conversão implícita entre outros tipos de ponto flutuante e o tipo `decimal` porque o tipo `decimal` tem maior precisão do que `float` ou `double`.

Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).

Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos de ponto flutuante](~/_csharplang/spec/types.md#floating-point-types)
- [O tipo decimal](~/_csharplang/spec/types.md#the-decimal-type)
- [Literais reais](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tipos integrais](integral-numeric-types.md)
- [Tabela de tipos internos](../keywords/built-in-types-table.md)
- [Numéricos no .NET](../../../standard/numerics.md)
- [Transmissões e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Tabela de formatação de resultados numéricos](../keywords/formatting-numeric-results-table.md)
- [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md)
