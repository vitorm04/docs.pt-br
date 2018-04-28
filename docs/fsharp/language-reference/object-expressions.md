---
title: Expressões de objeto (F#)
description: 'Aprenda a usar expressões de objeto do F # quando desejar evitar o código extra e sobrecarga necessária para criar um novo tipo nomeado.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f5a728823e7abe18aeb604b3991087fd0252698e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="object-expressions"></a><span data-ttu-id="90678-103">Expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="90678-103">Object Expressions</span></span>

<span data-ttu-id="90678-104">Um *objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que se baseia em um tipo base existente, uma interface ou um conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="90678-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="90678-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90678-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="90678-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="90678-106">Remarks</span></span>
<span data-ttu-id="90678-107">Na sintaxe anterior, o *typename* representa um tipo de classe existente ou um tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="90678-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="90678-108">*parâmetros de tipo* descreve os parâmetros de tipo genérico opcional.</span><span class="sxs-lookup"><span data-stu-id="90678-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="90678-109">O *argumentos* são usadas apenas para tipos de classe, que exigem parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="90678-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="90678-110">O *definições de membro* são substituições de métodos de classe base ou implementações de métodos abstratos de uma classe base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="90678-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="90678-111">O exemplo a seguir ilustra os diferentes tipos de expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="90678-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="90678-112">Usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="90678-112">Using Object Expressions</span></span>
<span data-ttu-id="90678-113">Você usa expressões de objeto quando você deseja evitar a sobrecarga que é necessário para criar um novo tipo nomeado e código extra.</span><span class="sxs-lookup"><span data-stu-id="90678-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="90678-114">Se você usar expressões de objeto para minimizar o número de tipos criada em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos.</span><span class="sxs-lookup"><span data-stu-id="90678-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="90678-115">Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="90678-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="90678-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90678-116">See Also</span></span>
[<span data-ttu-id="90678-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="90678-117">F# Language Reference</span></span>](index.md)
