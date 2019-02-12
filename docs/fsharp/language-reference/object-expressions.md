---
title: Expressões de objeto
description: Saiba como usar F# expressões de objeto quando você quer evitar o código extra e a sobrecarga necessária para criar um novo tipo nomeado.
ms.date: 02/08/2019
ms.openlocfilehash: c00b2e329a97b86ec2c8c84c143d2aa199875442
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091663"
---
# <a name="object-expressions"></a><span data-ttu-id="4b535-103">Expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="4b535-103">Object Expressions</span></span>

<span data-ttu-id="4b535-104">Uma *do objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que é baseada em um tipo base existente, interface ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="4b535-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b535-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b535-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4b535-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b535-106">Remarks</span></span>

<span data-ttu-id="4b535-107">Na sintaxe anterior, o *typename* representa um tipo de interface ou tipo de classe existente.</span><span class="sxs-lookup"><span data-stu-id="4b535-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="4b535-108">*parâmetros de tipo* descreve os parâmetros de tipo genérico opcional.</span><span class="sxs-lookup"><span data-stu-id="4b535-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="4b535-109">O *argumentos* são usados apenas para tipos de classe, que exigem parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="4b535-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="4b535-110">O *definições de membro* são substituições dos métodos da classe base ou implementações de método abstrato de uma classe base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="4b535-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="4b535-111">O exemplo a seguir ilustra vários tipos diferentes de expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="4b535-111">The following example illustrates several different types of object expressions.</span></span>

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

// This object expression implements multiple interfaces.
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements an interface chain.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a><span data-ttu-id="4b535-112">Usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="4b535-112">Using Object Expressions</span></span>

<span data-ttu-id="4b535-113">Você usar expressões de objeto quando você quer evitar o código extra e uma sobrecarga que é necessária para criar um novo tipo nomeado.</span><span class="sxs-lookup"><span data-stu-id="4b535-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="4b535-114">Se você usar expressões de objeto para minimizar o número de tipos criados em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos.</span><span class="sxs-lookup"><span data-stu-id="4b535-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="4b535-115">Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza a um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="4b535-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b535-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b535-116">See also</span></span>

- [<span data-ttu-id="4b535-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4b535-117">F# Language Reference</span></span>](index.md)
