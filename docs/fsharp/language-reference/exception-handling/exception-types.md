---
title: "Tipos de exceção (F#)"
description: "Saiba como definir e usar tipos de exceção F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="19960-104">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="19960-104">Exception Types</span></span>

<span data-ttu-id="19960-105">Há duas categorias de exceções em F #: tipos de exceção do .NET e tipos de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="19960-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="19960-106">Este tópico descreve como definir e usar tipos de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="19960-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="19960-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19960-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="19960-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="19960-108">Remarks</span></span>
<span data-ttu-id="19960-109">Na sintaxe anterior, *tipo de exceção* é o nome de um novo F # tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gera uma exceção desse tipo.</span><span class="sxs-lookup"><span data-stu-id="19960-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="19960-110">Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.</span><span class="sxs-lookup"><span data-stu-id="19960-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="19960-111">Uma definição típica para uma exceção F # é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="19960-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="19960-112">Você pode gerar uma exceção desse tipo usando o `raise` função, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="19960-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="19960-113">Você pode usar um tipo de exceção F # diretamente nos filtros em um `try...with` expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="19960-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="19960-114">O tipo de exceção que você definir com a `exception` palavra-chave em F # é um novo tipo que herda de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="19960-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="19960-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19960-115">See Also</span></span>
[<span data-ttu-id="19960-116">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="19960-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="19960-117">Exceções: a função `raise`</span><span class="sxs-lookup"><span data-stu-id="19960-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="19960-118">Hierarquia de exceções</span><span class="sxs-lookup"><span data-stu-id="19960-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
