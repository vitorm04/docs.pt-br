---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: Visão geral sobre os tipos de ponto flutuante internos do C#
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664186"
---
# <a name="floating-point-numeric-types-c-reference"></a>Tipos numéricos de ponto flutuante (Referência de C#)

Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#floating-point-literals). Todos os tipos de ponto flutuante também são tipos de valor. Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md) [de comparação e de igualdade](../operators/equality-operators.md).

A tabela a seguir mostra os intervalos de precisão e aproximados para os tipos de ponto flutuante:
  
|Tipo|Intervalo aproximado|Precisão|  
|----------|-----------------------|---------------|  
|`float`|±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup>|Aproximadamente de 6 a 9 dígitos|  
|`double`|±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup>|Aproximadamente de 15 a 17 dígitos|  
|`decimal`|±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup>|28 a 29 dígitos|  

O valor padrão para todos os tipos de ponto flutuante é `0`. Cada um dos tipos de ponto flutuante tem constantes denominadas `MinValue` e `MaxValue` para o valor mínimo e máximo desse tipo. Os tipos `float` e `double` têm outras constantes para `PositiveInfinity`, `NegativeInfinity`e `NaN` (para "Não é um número"). O tipo `decimal` inclui constantes para `Zero`, `One` e `MinusOne`.

O tipo `decimal` tem mais precisão e um intervalo menor do que `float` e `double`, o que o torna apropriado para cálculos financeiros e monetários.

É possível misturar tipos integrais e de ponto flutuante em uma expressão. Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante. A avaliação da expressão é executada de acordo com as regras a seguir:

- Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.
- Se não houver nenhum tipo `double` na expressão, ela será avaliada como `float` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.

Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:

- Zero positivo e negativo
- Infinito positivo e negativo
- Valor NaN (não é um número)
- O conjunto finito de valores diferentes de zero

Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).

É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.

## <a name="floating-point-literals"></a>Literais de ponto flutuante

Por padrão, um literal numérico de ponto flutuante no lado direito do operador de atribuição é tratado como `double`. É possível usar sufixos para converter um literal integral ou de ponto flutuante em um tipo específico:

- O sufixo `d` ou `D` converte um literal em um `double`.
- O sufixo `f` ou `F` converte um literal em um `float`.
- O sufixo `m` ou `M` converte um literal em um `decimal`.

Os exemplos a seguir mostram cada sufixo:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita (chamada de *conversão de expansão*) de `float` em `double` porque o intervalo dos valores `float` é um subconjunto adequado de `double` e não há perda de precisão de `float` para `double`. 

É necessário usar uma conversão explícita para converter um tipo de ponto flutuante em outro quando uma conversão implícita não está definida do tipo de origem para o tipo de destino. Isso é chamado de *conversão de estreitamento*. O caso explícito é necessário porque a conversão pode resultar em perda de dados. Não há conversão implícita entre outros tipos de ponto flutuante e o tipo `decimal` porque o tipo `decimal` tem maior precisão do que `float` ou `double`.

Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).

Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tipos integrais](integral-numeric-types.md)
- [Tabela de valores padrão](../keywords/default-values-table.md)
- [Tabela de formatação de resultados numéricos](../keywords/formatting-numeric-results-table.md)
- [Tabela de tipos internos](../keywords/built-in-types-table.md)
- [Numéricos no .NET](../../../standard/numerics.md)
- [Transmissões e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md)
- [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Cadeias de Caracteres de Formato Numérico Padrão](../../../standard/base-types/standard-numeric-format-strings.md)
