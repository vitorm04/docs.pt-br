---
title: Conversões cast e conversões
description: Saiba como a F# linguagem de programação fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543580"
---
# <a name="casting-and-conversions-f"></a>Conversões cast e conversões (F#)

Este tópico descreve o suporte para conversões de tipo F#no.

## <a name="arithmetic-types"></a>Tipos aritméticos

F#fornece operadores de conversão para conversões aritméticas entre vários tipos primitivos, como entre os tipos de ponto flutuante e inteiro. Os operadores de conversão integral e Char marcaram e desmarcaram formulários; os operadores de ponto flutuante e o operador de conversão de `enum` não. Os formulários desmarcados são definidos no `Microsoft.FSharp.Core.Operators` e os formulários marcados são definidos em `Microsoft.FSharp.Core.Operators.Checked`. Os formulários marcados verificam o estouro e geram uma exceção de tempo de execução se o valor resultante exceder os limites do tipo de destino.

Cada um desses operadores tem o mesmo nome que o nome do tipo de destino. Por exemplo, no código a seguir, no qual os tipos são anotados explicitamente, `byte` aparece com dois significados diferentes. A primeira ocorrência é o tipo e o segundo é o operador de conversão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

A tabela a seguir mostra os operadores de F#conversão definidos no.

|Operador|DESCRIÇÃO|
|--------|-----------|
|`byte`|Converter em byte, um tipo sem sinal de 8 bits.|
|`sbyte`|Converter em byte assinado.|
|`int16`|Converter em um inteiro com sinal de 16 bits.|
|`uint16`|Converta em um inteiro de 16 bits sem sinal.|
|`int32, int`|Converter em um número inteiro de 32 bits assinado.|
|`uint32`|Converter em um inteiro sem sinal de 32 bits.|
|`int64`|Converter em um número inteiro de 64 bits assinado.|
|`uint64`|Converter em um inteiro sem sinal de 64 bits.|
|`nativeint`|Converter em um inteiro nativo.|
|`unativeint`|Converter em um inteiro nativo não assinado.|
|`float, double`|Converter em um número de ponto flutuante IEEE de precisão dupla de 64 bits.|
|`float32, single`|Converter em um número de ponto flutuante IEEE de precisão simples de 32 bits.|
|`decimal`|Converter em `System.Decimal`.|
|`char`|Converter em `System.Char`, um caractere Unicode.|
|`enum`|Converter em um tipo enumerado.|

Além dos tipos primitivos internos, você pode usar esses operadores com tipos que implementam `op_Explicit` ou `op_Implicit` métodos com assinaturas apropriadas. Por exemplo, o operador de conversão de `int` funciona com qualquer tipo que fornece um método estático `op_Explicit` que usa o tipo como um parâmetro e retorna `int`. Como uma exceção especial para a regra geral que os métodos não podem ser sobrecarregados por tipo de retorno, você pode fazer isso para `op_Explicit` e `op_Implicit`.

## <a name="enumerated-types"></a>Tipos enumerados

O operador `enum` é um operador genérico que usa um parâmetro de tipo que representa o tipo de `enum` para converter. Quando ele é convertido em um tipo enumerado, as tentativas de inferência de tipos determinam o tipo de `enum` para o qual você deseja converter. No exemplo a seguir, a variável `col1` não é anotada explicitamente, mas seu tipo é inferido do teste de igualdade posterior. Portanto, o compilador pode deduzir que você está convertendo para uma enumeração `Color`. Como alternativa, você pode fornecer uma anotação de tipo, como com `col2` no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Você também pode especificar o tipo de enumeração de destino explicitamente como um parâmetro de tipo, como no código a seguir:

```fsharp
let col3 = enum<Color> 3
```

Observe que as conversões de enumeração só funcionam se o tipo subjacente da enumeração for compatível com o tipo que está sendo convertido. No código a seguir, a conversão não é compilada devido à incompatibilidade entre `int32` e `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Para obter mais informações, consulte [enumerações](enumerations.md).

## <a name="casting-object-types"></a>Convertendo tipos de objeto

A conversão entre os tipos em uma hierarquia de objetos é fundamental para a programação orientada a objeto. Há dois tipos básicos de conversões: a conversão (upmissing) e a conversão para baixo (Downcasting). A conversão de uma hierarquia significa converter de uma referência de objeto derivado para uma referência de objeto base. Essa conversão é garantida para funcionar contanto que a classe base esteja na hierarquia de herança da classe derivada. A projeção de uma hierarquia, de uma referência de objeto base para uma referência de objeto derivado, só terá sucesso se o objeto realmente for uma instância do tipo de destino (derivado) correto ou um tipo derivado do tipo de destino.

F#fornece operadores para esses tipos de conversões. O operador de `:>` converte a hierarquia e o operador de `:?>` converte a hierarquia.

### <a name="upcasting"></a>Convertendo

Em muitas linguagens orientadas a objeto, a reformulação é implícita; no F#, as regras são um pouco diferentes. A conversão é aplicada automaticamente quando você passa argumentos para métodos em um tipo de objeto. No entanto, para as funções que permitem associar em um módulo, a conversão não é automática, a menos que o tipo de parâmetro seja declarado como um tipo flexível. Para obter mais informações, consulte [tipos flexíveis](flexible-Types.md).

O operador de `:>` executa uma conversão estática, o que significa que o sucesso da conversão é determinado no momento da compilação. Se uma conversão que usa `:>` compila com êxito, ela é uma conversão válida e não tem chance de falha no tempo de execução.

Você também pode usar o operador de `upcast` para executar tal conversão. A expressão a seguir especifica uma conversão na hierarquia:

```fsharp
upcast expression
```

Quando você usa o operador upcast, o compilador tenta inferir o tipo que você está convertendo do contexto. Se o compilador não puder determinar o tipo de destino, o compilador relatará um erro. Uma anotação de tipo pode ser necessária.

### <a name="downcasting"></a>Downcasting

O operador de `:?>` executa uma conversão dinâmica, o que significa que o sucesso da conversão é determinado em tempo de execução. Uma conversão que usa o operador de `:?>` não é verificada no momento da compilação; Mas, em tempo de execução, é feita uma tentativa de conversão para o tipo especificado. Se o objeto for compatível com o tipo de destino, a conversão será realizada com sucesso. Se o objeto não for compatível com o tipo de destino, o tempo de execução gerará um `InvalidCastException`.

Você também pode usar o operador de `downcast` para executar uma conversão dinâmica de tipo. A expressão a seguir especifica uma conversão na hierarquia para um tipo inferido do contexto do programa:

```fsharp
downcast expression
```

Como para o operador de `upcast`, se o compilador não puder inferir um tipo de destino específico do contexto, ele relatará um erro. Uma anotação de tipo pode ser necessária.

O código a seguir ilustra o uso dos operadores `:>` e `:?>`. O código ilustra que o operador de `:?>` é mais bem usado quando você sabe que a conversão terá êxito, pois ele gera `InvalidCastException` se a conversão falhar. Se você não souber que uma conversão terá sucesso, um teste de tipo que usa uma expressão `match` é melhor porque evita a sobrecarga de gerar uma exceção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Como os operadores genéricos `downcast` e `upcast` contam com a inferência de tipos para determinar o argumento e o tipo de retorno, no código acima, você pode substituir

```fsharp
let base1 = d1 :> Base1
```

por

```fsharp
let base1: Base1 = upcast d1
```

Observe que uma anotação de tipo é necessária, pois `upcast` por si só não pôde determinar a classe base.

## <a name="see-also"></a>Confira também

- [Referência da Linguagem F#](index.md)
