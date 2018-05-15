---
title: Expressões de objeto (F#)
description: 'Aprenda a usar expressões de objeto do F # quando desejar evitar o código extra e sobrecarga necessária para criar um novo tipo nomeado.'
ms.date: 05/16/2016
ms.openlocfilehash: fed78e2be52838eedf55759b195696f1210a8a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="object-expressions"></a><span data-ttu-id="e8e86-103">Expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="e8e86-103">Object Expressions</span></span>

<span data-ttu-id="e8e86-104">Um *objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que se baseia em um tipo base existente, uma interface ou um conjunto de interfaces.</span><span class="sxs-lookup"><span data-stu-id="e8e86-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="e8e86-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8e86-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="e8e86-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8e86-106">Remarks</span></span>
<span data-ttu-id="e8e86-107">Na sintaxe anterior, o *typename* representa um tipo de classe existente ou um tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="e8e86-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="e8e86-108">*parâmetros de tipo* descreve os parâmetros de tipo genérico opcional.</span><span class="sxs-lookup"><span data-stu-id="e8e86-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="e8e86-109">O *argumentos* são usadas apenas para tipos de classe, que exigem parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="e8e86-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="e8e86-110">O *definições de membro* são substituições de métodos de classe base ou implementações de métodos abstratos de uma classe base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="e8e86-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="e8e86-111">O exemplo a seguir ilustra os diferentes tipos de expressões de objeto.</span><span class="sxs-lookup"><span data-stu-id="e8e86-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="e8e86-112">Usando expressões de objeto</span><span class="sxs-lookup"><span data-stu-id="e8e86-112">Using Object Expressions</span></span>
<span data-ttu-id="e8e86-113">Você usa expressões de objeto quando você deseja evitar a sobrecarga que é necessário para criar um novo tipo nomeado e código extra.</span><span class="sxs-lookup"><span data-stu-id="e8e86-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="e8e86-114">Se você usar expressões de objeto para minimizar o número de tipos criada em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos.</span><span class="sxs-lookup"><span data-stu-id="e8e86-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="e8e86-115">Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="e8e86-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="e8e86-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e86-116">See Also</span></span>
[<span data-ttu-id="e8e86-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="e8e86-117">F# Language Reference</span></span>](index.md)
