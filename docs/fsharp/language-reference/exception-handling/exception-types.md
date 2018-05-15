---
title: Tipos de exceção (F#)
description: 'Saiba como definir e usar tipos de exceção F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="exception-types"></a><span data-ttu-id="6ee45-103">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="6ee45-103">Exception Types</span></span>

<span data-ttu-id="6ee45-104">Há duas categorias de exceções em F #: tipos de exceção do .NET e tipos de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="6ee45-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="6ee45-105">Este tópico descreve como definir e usar tipos de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="6ee45-105">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="6ee45-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ee45-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="6ee45-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ee45-107">Remarks</span></span>
<span data-ttu-id="6ee45-108">Na sintaxe anterior, *tipo de exceção* é o nome de um novo F # tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gera uma exceção desse tipo.</span><span class="sxs-lookup"><span data-stu-id="6ee45-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="6ee45-109">Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.</span><span class="sxs-lookup"><span data-stu-id="6ee45-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="6ee45-110">Uma definição típica para uma exceção F # é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="6ee45-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="6ee45-111">Você pode gerar uma exceção desse tipo usando o `raise` função, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="6ee45-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="6ee45-112">Você pode usar um tipo de exceção F # diretamente nos filtros em um `try...with` expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ee45-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="6ee45-113">O tipo de exceção que você definir com a `exception` palavra-chave em F # é um novo tipo que herda de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="6ee45-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="6ee45-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ee45-114">See Also</span></span>
[<span data-ttu-id="6ee45-115">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="6ee45-115">Exception Handling</span></span>](index.md)

[<span data-ttu-id="6ee45-116">Exceções: a função `raise`</span><span class="sxs-lookup"><span data-stu-id="6ee45-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="6ee45-117">Hierarquia de exceções</span><span class="sxs-lookup"><span data-stu-id="6ee45-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
