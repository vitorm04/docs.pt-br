---
title: Expressões de objeto
description: Saiba como usar F# expressões de objeto quando você quer evitar o código extra e a sobrecarga necessária para criar um novo tipo nomeado.
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613915"
---
# <a name="object-expressions"></a><span data-ttu-id="17e16-103">Expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="17e16-103">Object Expressions</span></span>

<span data-ttu-id="17e16-104">Uma *do objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que é baseada em um tipo base existente, interface ou conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="17e16-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="17e16-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17e16-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="17e16-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="17e16-106">Remarks</span></span>

<span data-ttu-id="17e16-107">Na sintaxe anterior, o *typename* representa um tipo de interface ou tipo de classe existente.</span><span class="sxs-lookup"><span data-stu-id="17e16-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="17e16-108">*parâmetros de tipo* descreve os parâmetros de tipo genérico opcional.</span><span class="sxs-lookup"><span data-stu-id="17e16-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="17e16-109">O *argumentos* são usados apenas para tipos de classe, que exigem parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="17e16-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="17e16-110">O *definições de membro* são substituições dos métodos da classe base ou implementações de método abstrato de uma classe base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="17e16-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="17e16-111">O exemplo a seguir ilustra vários tipos diferentes de expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="17e16-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="17e16-112">Usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="17e16-112">Using Object Expressions</span></span>

<span data-ttu-id="17e16-113">Você usar expressões de objeto quando você quer evitar o código extra e uma sobrecarga que é necessária para criar um novo tipo nomeado.</span><span class="sxs-lookup"><span data-stu-id="17e16-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="17e16-114">Se você usar expressões de objeto para minimizar o número de tipos criados em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos.</span><span class="sxs-lookup"><span data-stu-id="17e16-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="17e16-115">Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza a um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="17e16-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="17e16-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17e16-116">See also</span></span>

- [<span data-ttu-id="17e16-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="17e16-117">F# Language Reference</span></span>](index.md)