---
title: Unidades de medida (F#)
description: 'Saiba como flutuante ponto e valores de inteiro em F # podem ter associadas a unidades de medida, que normalmente são usadas para indicar o comprimento, volume e massa.'
ms.date: 05/16/2016
ms.openlocfilehash: 3e47c92100c1dd99161be709a065913f501854f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564945"
---
# <a name="units-of-measure"></a>Unidades de medida

Flutuante ponto e valores inteiros com sinal em F # pode ter associado unidades de medida, que normalmente são usadas para indicar o comprimento, volume, em massa, e assim por diante. Usando as quantidades com unidades, habilitar o compilador verificar se relações aritméticas tem as unidades corretas, que ajuda a evitar erros de programação.


## <a name="syntax"></a>Sintaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Comentários
Define a sintaxe anterior *-o nome da unidade* como uma unidade de medida. A parte opcional é usada para definir uma nova medida em termos de unidades definidas anteriormente. Por exemplo, a linha a seguir define a medida `cm` (centímetro).

```fsharp
[<Measure>] type cm
```

A linha a seguir define a medida `ml` (milliliter) como um centímetro cúbico (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

Na sintaxe anterior, *medidas* é uma fórmula que envolve unidades. Em fórmulas que envolvam unidades, integrais potências têm suporte (positivos e negativos), espaços entre unidades indicam um produto de duas unidades, `*` também indica um produto de unidades, e `/` indica um quociente de unidades. Para uma unidade recíproca, você pode usar uma potência de número inteiro negativo ou um `/` que indica uma separação entre o numerador e o denominador de uma fórmula de unidade. Várias unidades no denominador devem estar entre parênteses. Unidades separadas por espaços após um `/` são interpretados como sendo parte do denominador, mas todas as unidades a seguir um `*` são interpretados como sendo parte do numerador.

Você pode usar 1 em expressões de unidade, apenas para indicar uma quantidade sem dimensão, ou em conjunto com outras unidades, como o numerador. Por exemplo, as unidades para uma taxa poderiam ser escritas como `1/s`, onde `s` indica segundos. Parênteses não são usados em fórmulas de unidade. Você não especificar constantes de conversão numérica nas fórmulas unidade; No entanto, você pode definir constantes de conversão com unidades separadamente e usá-los em cálculos verificada a unidade.

Fórmulas de unidade que têm o mesmo significado podem ser escritas em várias formas equivalentes. Portanto, o compilador converte fórmulas de unidade em um formato consistente, que converte potências negativas recíprocos, unidades de grupos em um único numerador e um denominador e coloca em ordem alfabética as unidades no numerador e o denominador.

Por exemplo, as fórmulas de unidade `kg m s^-2` e `m /s s * kg` são convertidos em `kg m/s^2`.

Você pode usar unidades de medida em expressões de ponto flutuante. Usar números de ponto flutuante junto com as unidades associadas de medida adiciona outro nível de segurança de tipos e ajuda a evitar os erros de incompatibilidade de unidade que podem ocorrer em fórmulas quando você usa números de ponto flutuante sem rigidez de tipos. Se você gravar um flutuante ponto expressão que usa unidades, as unidades na expressão devem corresponder.

Você pode anotar literais com uma fórmula de unidade entre colchetes, como mostrado nos exemplos a seguir.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Você não colocar um espaço entre o número e o colchete angular; No entanto, você pode incluir um sufixo literal, como `f`, conforme mostrado no exemplo a seguir.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Tal uma anotação altera o tipo do literal do seu tipo primitivo (como `float`) em um tipo dimensionado, tais como `float<cm>` ou, nesse caso, `float<miles/hour>`. A anotação de uma unidade de `<1>` indica uma quantidade sem dimensão e seu tipo é equivalente ao tipo primitivo sem um parâmetro de unidade.

O tipo de uma unidade de medida é um ponto flutuante ou tipo signed integral junto com uma anotação de unidade extra, indicado entre parênteses. Portanto, quando você escreve o tipo de uma conversão de `g` (gramas) para `kg` (kg), descreve os tipos da seguinte maneira.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Unidades de medida são usadas para a verificação de unidade de tempo de compilação, mas não são mantidas no ambiente de tempo de execução. Portanto, elas não afetam o desempenho.

Unidades de medida podem ser aplicadas a qualquer tipo flutuante não apenas os tipos de ponto; No entanto, somente tipos de ponto flutuante assinado tipos integrais e quantidades de suporte dimensionada tipos decimais. Portanto, só faz sentido usar unidades de medida, os tipos primitivos e agregações que contêm esses tipos primitivos.

O exemplo a seguir ilustra o uso das unidades de medida.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
O exemplo de código a seguir ilustra como converter de um número de ponto flutuante sem dimensão em um valor de ponto flutuante dimensionadas. Você apenas multiplicar 1.0, aplicando as dimensões para o 1.0. Isso pode ser abstract em uma função como `degreesFahrenheit`.

Além disso, quando você passar valores dimensionados para funções que esperam sem dimensão números de ponto flutuante, você deve cancelar às unidades ou convertido `float` usando o `float` operador. Neste exemplo, você dividir por `1.0<degC>` para os argumentos para `printf` porque `printf` espera quantidades sem dimensão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

A sessão de exemplo a seguir mostra as saídas de e entradas para este código.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Usando unidades genéricas
Você pode escrever funções genéricas que operam nos dados que tenha uma unidade de medida associada. Isso é feito especificando um tipo junto com uma unidade genérico como um parâmetro de tipo, conforme mostrado no exemplo de código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>Criando tipos de agregação com unidades genéricas
O código a seguir mostra como criar um tipo de agregação que consiste em individuais valores de ponto flutuante com unidades genéricos. Isso permite que um único tipo a ser criado que funciona com uma variedade de unidades. Além disso, unidades genéricas preservam a segurança de tipo, garantindo que um tipo genérico que tem um conjunto de unidades é um tipo diferente do mesmo tipo genérico com um conjunto diferente de unidades. A base dessa técnica é que o `Measure` atributo pode ser aplicado ao parâmetro de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>Unidades em tempo de execução
Unidades de medida são usadas para verificação de tipo estático. Quando valores de ponto flutuante são compilados, as unidades de medida são eliminadas, assim, as unidades são perdidas em tempo de execução. Portanto, qualquer tentativa para implementar a funcionalidade que depende de verificação de unidades de tempo de execução não é possível. Por exemplo, Implementando um `ToString` função imprimir as unidades não é possível.


## <a name="conversions"></a>Conversões
Para converter um tipo que possui unidades (por exemplo, `float<'u>`) para um tipo que não tem unidades, você pode usar a função de conversão padrão. Por exemplo, você pode usar `float` para converter para um `float` valor que não tem unidades, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Para converter um valor sem unidade em um valor que tem unidades, você pode multiplicar por um valor de 1 ou 1.0 é anotado com unidades apropriadas. No entanto, para gravar as camadas de interoperabilidade, também há algumas funções explícita que você pode usar para converter valores sem unidade para valores com unidades. Eles estão no [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) módulo. Por exemplo, para converter de sem uma unidade `float` para um `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a>Unidades de medida no pacote de energia F #
Uma biblioteca de unidade está disponível na PowerPack F #. A biblioteca de unidade inclui unidades SI e constantes físicas.


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
