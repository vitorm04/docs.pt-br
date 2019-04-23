---
title: Expressões de objeto
description: Saiba como usar F# expressões de objeto quando você quer evitar o código extra e a sobrecarga necessária para criar um novo tipo nomeado.
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157839"
---
# <a name="object-expressions"></a>Expressões de objeto

Uma *do objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que é baseada em um tipo base existente, interface ou conjunto de interfaces.

## <a name="syntax"></a>Sintaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *typename* representa um tipo de interface ou tipo de classe existente. *parâmetros de tipo* descreve os parâmetros de tipo genérico opcional. O *argumentos* são usados apenas para tipos de classe, que exigem parâmetros do construtor. O *definições de membro* são substituições dos métodos da classe base ou implementações de método abstrato de uma classe base ou uma interface.

O exemplo a seguir ilustra vários tipos diferentes de expressões de objeto.

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>Usando expressões de objeto

Você usar expressões de objeto quando você quer evitar o código extra e uma sobrecarga que é necessária para criar um novo tipo nomeado. Se você usar expressões de objeto para minimizar o número de tipos criados em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos. Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza a um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
