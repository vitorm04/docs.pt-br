---
title: Opções de valores
description: Saiba mais sobre F# o tipo de opção de valor, que é uma versão de struct do tipo de opção.
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424014"
---
# <a name="value-options"></a>Opções de valores

O tipo de opção de F# valor em é usado quando as duas circunstâncias a seguir têm:

1. Um cenário é apropriado para uma [ F# opção](options.md).
2. O uso de uma estrutura fornece um benefício de desempenho em seu cenário.

Nem todos os cenários sensíveis ao desempenho são "resolvidos" usando structs. Você deve considerar o custo adicional de copiar ao usá-los em vez de tipos de referência. No entanto F# , programas grandes normalmente instanciam muitos tipos opcionais que fluem por meio de caminhos ativos e, nesses casos, as estruturas geralmente podem produzir melhor desempenho geral durante o tempo de vida de um programa.

## <a name="definition"></a>Definição

A opção Value é definida como uma [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions) que é semelhante ao tipo de opção de referência. Sua definição pode ser considerada desta forma:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Opção de valor está de acordo com a igualdade estrutural e a comparação. A principal diferença é que o nome compilado, o nome do tipo e os nomes de caso indicam que ele é um tipo de valor.

## <a name="using-value-options"></a>Usando opções de valor

As opções de valor são usadas apenas como [Opções](options.md). `ValueSome` é usado para indicar que um valor está presente e `ValueNone` é usado quando um valor não está presente:

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

Assim como acontece com [Opções](options.md), a Convenção de nomenclatura para uma função que retorna `ValueOption` é prefixada com `try`.

## <a name="value-option-properties-and-methods"></a>Métodos e propriedades da opção de valor

Há uma propriedade para opções de valor neste momento: `Value`. Um <xref:System.InvalidOperationException> será gerado se nenhum valor estiver presente quando essa propriedade for chamada.

## <a name="value-option-functions"></a>Funções de opção de valor

Atualmente, há uma função com limite de módulo para opções de valor, `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

Assim como ocorre com a função `defaultArg`, `defaultValueArg` retorna o valor subjacente da opção de valor fornecido, se existir; caso contrário, retornará o valor padrão especificado.

Neste momento, não há outras funções associadas ao módulo para as opções de valor.

## <a name="see-also"></a>Consulte também

- [Opções](options.md)
