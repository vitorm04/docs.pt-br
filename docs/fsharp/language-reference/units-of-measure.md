---
title: Unidades de medida
description: Saiba de ponto flutuante como e assinado valores inteiros F# podem ter associadas a unidades de medida, que normalmente são usadas para indicar o comprimento, volume e em massa.
ms.date: 05/16/2016
ms.openlocfilehash: 935dbff3545f92736ce8c51de86a168429dc194f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982534"
---
# <a name="units-of-measure"></a>Unidades de medida

Ponto flutuante e assinado valores inteiros F# podem ter associadas a unidades de medida, que normalmente são usadas para indicar o comprimento, volume, em massa e assim por diante. Ao usar as quantidades com unidades, você habilita o compilador verificar se o aritméticas relações tem as unidades corretas, que ajuda a evitar erros de programação.

## <a name="syntax"></a>Sintaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Comentários

A sintaxe anterior define *nome da unidade* como uma unidade de medida. A parte opcional é usada para definir uma nova medida em termos de unidades definidas anteriormente. Por exemplo, a linha a seguir define a medida `cm` (centímetro).

```fsharp
[<Measure>] type cm
```

A linha a seguir define a medida `ml` (milliliter) como um centímetro cúbico (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

Na sintaxe anterior, *medida* é uma fórmula que envolve a unidades. Em fórmulas que envolvem unidades, integrais potências têm suporte (positivo e negativo), espaços entre unidades indicam um produto de duas unidades, `*` também indica um produto de unidades, e `/` indica um quociente de unidades. Em uma unidade recíproca, você pode usar uma potência de número inteiro negativo ou um `/` que indica uma separação entre o numerador e o denominador de uma fórmula de unidade. Várias unidades no denominador devem ficar entre parênteses. Unidades separadas por espaços após um `/` são interpretados como parte do denominador, mas nenhuma unidade seguindo um `*` são interpretados como parte do numerador.

Você pode usar 1 em expressões de unidade, qualquer um sozinho para indicar uma quantidade sem dimensão, ou em conjunto com outras unidades, como o numerador. Por exemplo, as unidades para uma taxa seriam escritas como `1/s`, onde `s` indica segundos. Parênteses não são usados em fórmulas de unidade. Você não especificar constantes de conversão numérica nas fórmulas de unidade; No entanto, você pode definir constantes de conversão com unidades separadamente e usá-los em cálculos de unidade-checked.

Fórmulas de unidade que significam a mesma coisa podem ser escritas de várias maneiras equivalentes. Portanto, o compilador converte as fórmulas de unidade em um formato consistente, que converte potências negativas recíprocos, unidades de grupos em um único numerador e um denominador e coloca em ordem alfabética as unidades no numerador e do denominador.

Por exemplo, as fórmulas de unidade `kg m s^-2` e `m /s s * kg` são convertidos em `kg m/s^2`.

Você pode usar unidades de medida em expressões de ponto flutuante. Usar os números de ponto flutuante junto com as unidades associadas de medida adiciona outro nível de segurança de tipo e ajuda a evitar os erros de incompatibilidade de unidade que podem ocorrer em fórmulas quando você usa números de ponto flutuante sem rigidez de tipos. Se você escrever flutuante expressão de ponto que usa unidades, as unidades na expressão devem corresponder.

É possível anotar literais com uma fórmula de unidade em colchetes angulares, conforme mostrado nos exemplos a seguir.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Você não colocar um espaço entre o número e o colchete angular; No entanto, você pode incluir um sufixo literal, como `f`, conforme mostrado no exemplo a seguir.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Tal uma anotação altera o tipo do literal do seu tipo primitivo (como `float`) para um tipo dimensionado, tais como `float<cm>` ou, nesse caso, `float<miles/hour>`. A anotação de uma unidade de `<1>` indica uma quantidade sem dimensão e seu tipo é equivalente ao tipo primitivo sem um parâmetro de unidade.

O tipo de uma unidade de medida é um ponto flutuante ou integral tipo junto com uma anotação de unidade extra, indicada entre parênteses com sinal. Assim, quando você escreve o tipo de uma conversão de `g` (gramas) para `kg` (quilogramas), você descreve os tipos da seguinte maneira.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Unidades de medida são usadas para verificação de unidade de tempo de compilação, mas não são mantidas no ambiente de tempo de execução. Portanto, elas não afetam o desempenho.

Unidades de medida podem ser aplicadas a qualquer tipo, não apenas tipos de ponto; de flutuante No entanto, somente tipos de ponto flutuante assinado tipos integrais e quantidades de suporte dimensionada de tipos decimais. Portanto, só faz sentido usar unidades de medida dos tipos primitivos e agregações que contêm esses tipos primitivos.

O exemplo a seguir ilustra o uso de unidades de medida.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

O exemplo de código a seguir ilustra como converter de um número de ponto flutuante sem dimensão em um valor de ponto flutuante dimensionadas. Você apenas multiplicar por 1,0, aplicando as dimensões para a 1.0. Você pode abstrair isso em uma função como `degreesFahrenheit`.

Além disso, quando você passa valores dimensionadas para funções que esperam sem dimensão números de ponto flutuante, você deve cancelar a unidades ou convertido para `float` usando o `float` operador. Neste exemplo, dividir por `1.0<degC>` para os argumentos a serem `printf` porque `printf` espera que as quantidades sem dimensão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

A sessão de exemplo a seguir mostra as saídas do e entradas para este código.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Usando unidades genéricas

Você pode escrever funções genéricas que operam nos dados que tem uma unidade de medida associada. Fazer isso especificando um tipo junto com uma unidade genérico como um parâmetro de tipo, conforme mostrado no exemplo de código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Criar tipos de agregação com unidades genéricas

O código a seguir mostra como criar um tipo de agregação que consiste em individuais valores de ponto flutuante que têm unidades que são genéricas. Isso permite que um único tipo a ser criado que funciona com uma variedade de unidades. Além disso, unidades genéricas preservam a segurança de tipos, garantindo que um tipo genérico que tem um conjunto de unidades é um tipo diferente do mesmo tipo genérico com um conjunto diferente de unidades. A base dessa técnica é que o `Measure` atributo pode ser aplicado ao parâmetro de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Unidades em tempo de execução

Unidades de medida são usadas para verificação de tipo estático. Quando valores de ponto flutuante são compiladas, as unidades de medida são eliminadas, para que as unidades sejam perdidas em tempo de execução. Portanto, qualquer tentativa para implementar a funcionalidade que depende de verificando as unidades de tempo de execução não é possível. Por exemplo, Implementando um `ToString` função para imprimir as unidades não é possível.

## <a name="conversions"></a>Conversões

Para converter um tipo que tem as unidades (por exemplo, `float<'u>`) para um tipo que não tem unidades, você pode usar a função de conversão padrão. Por exemplo, você pode usar `float` para converter em um `float` valor que não tem unidades, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Para converter um valor sem unidade em um valor que tem as unidades, você pode multiplicar por um valor de 1 ou 1.0 é anotado com as unidades apropriadas. No entanto, para gravar as camadas de interoperabilidade, também há algumas funções explícita que você pode usar para converter valores sem unidade em valores com as unidades. Eles estão na [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) módulo. Por exemplo, para converter de um sem unidade `float` para um `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Unidades de medida no F# biblioteca principal

Uma biblioteca de unidade está disponível no `FSharp.Data.UnitSystems.SI` namespace. Ele inclui as unidades de SI em sua forma do símbolo (como `m` de medidor) na `UnitSymbols` namespace secundário e seu nome completo (como `meter` de medidor) na `UnitNames` namespace secundário.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)