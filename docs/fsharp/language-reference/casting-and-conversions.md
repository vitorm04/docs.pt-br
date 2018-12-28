---
title: Conversões cast e conversões
description: Saiba como o F# linguagem de programação fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos.
ms.date: 05/16/2016
ms.openlocfilehash: 2a12d48106a267edfc67c9e7b3d3a7bd41d8261c
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655979"
---
# <a name="casting-and-conversions-f"></a>Conversões cast e conversões (F#)

Este tópico descreve o suporte para conversões de tipo no F#.

## <a name="arithmetic-types"></a>Tipos aritméticos

F#Fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos, como entre inteiro e tipos de ponto flutuante. Os operadores de conversão integral e char verificou e formulários desmarcados; o ponto flutuante operadores e a `enum` operador de conversão não fizer isso. Os formulários não verificados são definidos no `Microsoft.FSharp.Core.Operators` e os formulários verificados são definidos em `Microsoft.FSharp.Core.Operators.Checked`. Os formulários verificados procurar estouro e geram uma exceção de tempo de execução se o valor resultante exceder os limites do tipo de destino.

Cada um desses operadores tem o mesmo nome que o nome do tipo de destino. Por exemplo, no código a seguir, no qual os tipos explicitamente são anotados, `byte` aparece com dois significados diferentes. A primeira ocorrência é o tipo e o segundo é o operador de conversão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

A tabela a seguir mostra os operadores de conversão definidos em F#.

|Operador|Descrição|
|--------|-----------|
|`byte`|Converta em bytes, um tipo sem sinal de 8 bits.|
|`sbyte`|Converta em byte assinado.|
|`int16`|Converta em um inteiro com sinal de 16 bits.|
|`uint16`|Converta em um inteiro sem sinal de 16 bits.|
|`int32, int`|Converta em um inteiro com sinal de 32 bits.|
|`uint32`|Converta em um inteiro sem sinal de 32 bits.|
|`int64`|Converta em um inteiro com sinal de 64 bits.|
|`uint64`|Converta em um inteiro sem sinal de 64 bits.|
|`nativeint`|Converta em um inteiro nativo.|
|`unativeint`|Converta em um inteiro sem sinal de nativo.|
|`float, double`|Converta em um IEEE de precisão dupla de 64 bits número de ponto flutuante.|
|`float32, single`|Converta em um IEEE de precisão simples de 32 bits número de ponto flutuante.|
|`decimal`|Converter em `System.Decimal`.|
|`char`|Converter em `System.Char`, um caractere Unicode.|
|`enum`|Converta em um tipo enumerado.|

Além dos tipos primitivos internos, você pode usar esses operadores com tipos que implementam `op_Explicit` ou `op_Implicit` métodos com assinaturas apropriadas. Por exemplo, o `int` operador de conversão funciona com qualquer tipo que fornece um método estático `op_Explicit` que usa o tipo como um parâmetro e retorna `int`. Como uma exceção especial para a regra geral que os métodos não podem ser sobrecarregados pelo tipo de retorno, você pode fazer isso para `op_Explicit` e `op_Implicit`.

## <a name="enumerated-types"></a>Tipos enumerados

O `enum` operador é um operador genérico que assume um parâmetro de tipo que representa o tipo do `enum` para converter em. Quando ele converte em um tipo enumerado, digite as tentativas para determinar o tipo de inferência de tipos de `enum` que você deseja converter. No exemplo a seguir, a variável `col1` não é anotado explicitamente, mas seu tipo é inferido do teste de igualdade posterior. Portanto, o compilador pode deduzir que você está convertendo para uma `Color` enumeração. Como alternativa, você pode fornecer uma anotação de tipo, assim como acontece com `col2` no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Você também pode especificar o tipo de enumeração de destino explicitamente como um parâmetro de tipo, como no código a seguir:

```fsharp
let col3 = enum<Color> 3
```

Observe que a enumeração converte trabalho somente se o tipo subjacente da enumeração é compatível com o tipo que está sendo convertido. No código a seguir, a conversão Falha na compilação devido a incompatibilidade entre `int32` e `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Para obter mais informações, consulte [enumerações](enumerations.md).

## <a name="casting-object-types"></a>Conversão de tipos de objeto

Conversão entre tipos em uma hierarquia de objetos é fundamental para programação orientada a objeto. Há dois tipos básicos de conversões: conversão para cima (upcasting) e de conversão para baixo (Baixar). Conversão de uma hierarquia significa que a conversão de uma referência de objeto derivado de uma referência ao objeto base. Uma conversão é garantida para funcionar, contanto que a classe base está na hierarquia de herança da classe derivada. Conversão de uma hierarquia, de uma referência de objeto base para uma referência de objeto derivado, só terá sucesso se o objeto é, na verdade, uma instância do tipo de destino correto (derivado) ou um tipo derivado do tipo de destino.

F#Fornece operadores para esses tipos de conversões. O `:>` operador converte até a hierarquia e o `:?>` operador converte abaixo na hierarquia.

### <a name="upcasting"></a>Upcasting

Em muitas linguagens orientadas a objeto, upcasting é implícita; no F#, as regras são ligeiramente diferentes. Upcasting é aplicada automaticamente quando você passar argumentos para métodos em um tipo de objeto. No entanto, para as funções permitem a associação em um módulo, upcasting não é automática, a menos que o tipo de parâmetro é declarado como um tipo flexível. Para obter mais informações, consulte [tipos flexíveis](flexible-Types.md).

O `:>` operador executa um estático cast, o que significa que o sucesso da conversão é determinado em tempo de compilação. Se uma conversão que usa `:>` será compilado com êxito, ele é uma conversão válida e não tem nenhuma possibilidade de falha em tempo de execução.

Você também pode usar o `upcast` operador para realizar essa conversão. A expressão a seguir especifica uma conversão até a hierarquia:

```fsharp
upcast expression
```

Quando você usa o operador upcast, o compilador tentará inferir o tipo que você estiver convertendo a partir do contexto. Se o compilador não puder determinar o tipo de destino, o compilador relatará um erro.

### <a name="downcasting"></a>Baixar

O `:?>` operador executa dinâmico cast, o que significa que o sucesso da conversão é determinado em tempo de execução. Uma conversão que usa o `:?>` operador não é verificado em tempo de compilação, mas em tempo de execução é feita uma tentativa de converter no tipo especificado. Se o objeto é compatível com o tipo de destino, a conversão for bem-sucedida. Se o objeto não é compatível com o tipo de destino, o tempo de execução gera uma `InvalidCastException`.

Você também pode usar o `downcast` operador para executar uma conversão de tipo dinâmico. A expressão a seguir especifica uma conversão de toda a hierarquia para um tipo que é inferido do contexto do programa:

```fsharp
downcast expression
```

Para o `upcast` operador, se o compilador não é possível inferir um tipo de destino específico do contexto, ele relatará um erro.

O código a seguir ilustra o uso do `:>` e `:?>` operadores. O código ilustra que o `:?>` operador é melhor usado quando você sabe que a conversão seja bem-sucedida, porque ele gerará `InvalidCastException` se a conversão falhar. Se você não souber que uma conversão seja bem-sucedida, um teste de tipo que usa um `match` expressão é melhor porque evita a sobrecarga de gerar uma exceção.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Porque os operadores genéricos `downcast` e `upcast` dependem a inferência de tipo para determinar o tipo de argumento e retornam, no código acima, você pode substituir

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
let base1 = upcast d1
```

No código anterior, o tipo de argumento e os tipos de retorno são `Derived1` e `Base1`, respectivamente.

Para obter mais informações sobre testes de tipo, consulte [expressões de correspondência](match-Expressions.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
