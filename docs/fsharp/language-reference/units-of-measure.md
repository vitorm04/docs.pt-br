---
title: Unidades de medida
description: Saiba como os valores de ponto flutuante e inteiro F# assinado no podem ter unidades de medida associadas, que normalmente são usadas para indicar comprimento, volume e massa.
ms.date: 05/16/2016
ms.openlocfilehash: f97eac9984f934c55aff8cf9f287afbc3aa098f3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630162"
---
# <a name="units-of-measure"></a>Unidades de medida

Os valores de ponto flutuante e inteiro F# assinado no podem ter unidades de medida associadas, que normalmente são usadas para indicar comprimento, volume, massa e assim por diante. Usando quantidades com unidades, você habilita o compilador para verificar se as relações aritméticas têm as unidades corretas, o que ajuda a evitar erros de programação.

## <a name="syntax"></a>Sintaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Comentários

A sintaxe anterior define o *nome da unidade* como uma unidade de medida. A parte opcional é usada para definir uma nova medida em termos de unidades definidas anteriormente. Por exemplo, a linha a seguir define a `cm` medida (centímetro).

```fsharp
[<Measure>] type cm
```

A linha a seguir define a `ml` medida (milliliter) como um centímetro cúbico`cm^3`().

```fsharp
[<Measure>] type ml = cm^3
```

Na sintaxe anterior, *Measure* é uma fórmula que envolve unidades. Em fórmulas que envolvem unidades, os poderes integrais têm suporte (positivo e negativo), os espaços entre as unidades indicam um `*` produto das duas unidades, também indica um `/` produto de unidades e indica um quociente de unidades. Para uma unidade recíproca, você pode usar uma potência de número inteiro negativo ou `/` um que indica uma separação entre o numerador e o denominador de uma fórmula de unidade. Várias unidades no denominador devem ser circundadas por parênteses. Unidades separadas por espaços depois de `/` um são interpretadas como parte do denominador, mas qualquer unidade `*` após a é interpretada como parte do numerador.

Você pode usar 1 em expressões de unidade, seja sozinho para indicar uma quantidade sem dimensão ou junto com outras unidades, como no numerador. Por exemplo, as unidades de uma taxa seriam gravadas como `1/s`, em `s` que indica segundos. Os parênteses não são usados em fórmulas de unidade. Você não especifica constantes de conversão numérica nas fórmulas de unidade; no entanto, você pode definir constantes de conversão com unidades separadamente e usá-las em cálculos de unidade verificada.

As fórmulas de unidade que significam a mesma coisa podem ser escritas de várias maneiras equivalentes. Portanto, o compilador converte fórmulas de unidade em um formato consistente, o que converte potências negativas em recíprocos, agrupa unidades em um único numerador e um denominador e alphabetizes as unidades no numerador e no denominador.

Por exemplo, as fórmulas `kg m s^-2` de `m /s s * kg` unidade e são ambas `kg m/s^2`convertidas para.

Você usa unidades de medida em expressões de ponto flutuante. O uso de números de ponto flutuante junto com as unidades de medida associadas adiciona outro nível de segurança de tipo e ajuda a evitar erros de incompatibilidade de unidade que podem ocorrer em fórmulas quando você usa números de ponto flutuante de tipo fraco. Se você escrever uma expressão de ponto flutuante que usa unidades, as unidades na expressão devem corresponder.

Você pode anotar literais com uma fórmula de unidade entre colchetes angulares, conforme mostrado nos exemplos a seguir.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Você não coloca um espaço entre o número e o colchete angular; no entanto, você pode incluir um sufixo `f`literal como, como no exemplo a seguir.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Tal anotação altera o tipo do literal de seu tipo primitivo ( `float`como) para um tipo dimensionável, `float<cm>` como ou, nesse caso, `float<miles/hour>`. Uma anotação de unidade `<1>` de indica uma quantidade sem dimensão, e seu tipo é equivalente ao tipo primitivo com um parâmetro de unidade.

O tipo de uma unidade de medida é um ponto flutuante ou um tipo integral assinado junto com uma anotação de unidade extra, indicada entre colchetes. Assim, ao gravar o tipo de uma conversão de `g` (gramas) em `kg` (quilogramas), você descreve os tipos da seguinte maneira.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Unidades de medida são usadas para verificação de unidade em tempo de compilação, mas não são mantidas no ambiente de tempo de execução. Portanto, eles não afetam o desempenho.

Unidades de medida podem ser aplicadas a qualquer tipo, não apenas a tipos de ponto flutuante; no entanto, somente os tipos de ponto flutuante, tipos integrais assinados e tipos decimais dão suporte a quantidades dimensionadas. Portanto, faz sentido usar unidades de medida nos tipos primitivos e em agregações que contêm esses tipos primitivos.

O exemplo a seguir ilustra o uso de unidades de medida.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

O exemplo de código a seguir ilustra como converter de um número de ponto flutuante de dimensão para um valor de ponto flutuante dimensionável. Você apenas multiplica por 1,0, aplicando as dimensões ao 1,0. Você pode abstrair isso em uma função `degreesFahrenheit`como.

Além disso, quando você passa valores dimensionados para funções que esperam números de ponto flutuante sem dimensão, você deve cancelar as unidades ou converter `float` para usando o `float` operador. Neste exemplo, você divide por `1.0<degC>` para os argumentos para porque `printf` `printf` o espera quantidades com dimensão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

A sessão de exemplo a seguir mostra as saídas de e entradas para esse código.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Usando unidades genéricas

Você pode escrever funções genéricas que operam em dados que têm uma unidade de medida associada. Você faz isso especificando um tipo junto com uma unidade genérica como um parâmetro de tipo, conforme mostrado no exemplo de código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Criando tipos de agregação com unidades genéricas

O código a seguir mostra como criar um tipo de agregação que consiste em valores de ponto flutuante individuais que têm unidades genéricas. Isso permite que um único tipo seja criado e funcione com uma variedade de unidades. Além disso, as unidades genéricas preservam a segurança do tipo, garantindo que um tipo genérico que tenha um conjunto de unidades seja um tipo diferente do mesmo tipo genérico com um conjunto diferente de unidades. A base dessa técnica é que o `Measure` atributo pode ser aplicado ao parâmetro de tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Unidades em tempo de execução

Unidades de medida são usadas para verificação de tipo estático. Quando os valores de ponto flutuante são compilados, as unidades de medida são eliminadas e, portanto, as unidades são perdidas no tempo de execução. Portanto, qualquer tentativa de implementar a funcionalidade que depende da verificação das unidades em tempo de execução não é possível. Por exemplo, a implementação `ToString` de uma função para imprimir as unidades não é possível.

## <a name="conversions"></a>Conversões

Para converter um tipo que tem unidades (por exemplo, `float<'u>`) em um tipo que não tem unidades, você pode usar a função de conversão padrão. Por exemplo, você pode usar `float` para converter para um `float` valor que não tem unidades, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Para converter um valor sem unidade em um valor que tem unidades, você pode multiplicar por um valor 1 ou 1,0 anotado com as unidades apropriadas. No entanto, para escrever camadas de interoperabilidade, há também algumas funções explícitas que você pode usar para converter valores sem unidade em valores com unidades. Eles estão no módulo [Microsoft. FSharp. Core. LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) . Por exemplo, para converter de uma unidade `float` para uma `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Unidades de medida na biblioteca F# principal

Uma biblioteca de unidades está disponível no `FSharp.Data.UnitSystems.SI` namespace. Ele inclui unidades de si no formato de símbolo (como `m` para o medidor) `UnitSymbols` no subnamespace e seu nome completo (como `meter` para o medidor) no `UnitNames` subnamespace.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
