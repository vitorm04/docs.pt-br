---
title: 'Opções de valor (F #)'
description: 'Saiba mais sobre o tipo de opção de valor de F #, que é uma versão de estrutura do tipo de opção.'
ms.date: 06/16/2018
ms.openlocfilehash: 4c255cbbcfd9cb480230de09cd370a401c87343a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42936580"
---
# <a name="value-options"></a>Opções de valor

O tipo de opção de valor em F # é usado quando mantém as duas circunstâncias a seguir:

1. Um cenário é adequado para um [opção de F #](options.md).
2. Usar um struct fornece um benefício de desempenho em seu cenário.

Nem todos os cenários sensíveis a desempenho são "resolvidos" usando structs. Você deve considerar o custo adicional de cópia quando usá-los em vez de tipos de referência. No entanto, grandes programas em F # geralmente instanciar muitos tipos opcionais que fluem por meio de caminhos de acesso, pois structs, às vezes, pode gerar o melhor desempenho geral ao longo do tempo de vida de um programa.

## <a name="definition"></a>Definição

Opção de valor é definida como um [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions) que é semelhante ao tipo de opção de referência:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpValueOption`1")>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone: 'T voption
    | ValueSome: 'T -> 'T voption

    member Value : 'T

and 'T voption = ValueOption<'T>
```

Opção de valor está em conformidade com a comparação e igualdade estrutural. A principal diferença é que o nome compilado, o nome do tipo e o casos nomes indicam que ele é um tipo de valor.

## <a name="using-value-options"></a>Usando as opções de valor

Opções de valor são usadas exatamente como qualquer [opções](options.md). `ValueSome` é usado para indicar que um valor está presente, e `ValueNone` é usado quando um valor não está presente:

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

Assim como acontece com [opções](options.md), a convenção de nomenclatura para uma função que retorna `ValueOption` é um prefixo com `try`.

## <a name="value-option-properties-and-methods"></a>Métodos e propriedades do valor de opção

Há uma propriedade para opções de valor no momento: `Value`. Um <xref:System.InvalidOperationException> será gerado se nenhum valor está presente quando essa propriedade é invocada.

## <a name="value-option-functions"></a>Funções com valor de opção

Atualmente, há uma função de módulo associada para opções de valor, `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

Assim como acontece com o `defaultArg` função, `defaultValueArg` retorna o valor subjacente da opção de valor determinado, se ela existir; caso contrário, ele retornará o valor padrão especificado.

Neste momento, não há nenhuma outra função do módulo associado para opções de valor.

## <a name="see-also"></a>Consulte também

[Opções](options.md)