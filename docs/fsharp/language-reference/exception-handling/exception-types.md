---
title: Tipos de exceção (F#)
description: Saiba como definir e usar tipos de exceção do F#.
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858815"
---
# <a name="exception-types"></a><span data-ttu-id="c2d84-103">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="c2d84-103">Exception Types</span></span>

<span data-ttu-id="c2d84-104">Há duas categorias de exceções em F#: tipos de exceção do .NET e tipos de exceção do F#.</span><span class="sxs-lookup"><span data-stu-id="c2d84-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="c2d84-105">Este tópico descreve como definir e usar tipos de exceção do F#.</span><span class="sxs-lookup"><span data-stu-id="c2d84-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2d84-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2d84-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="c2d84-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2d84-107">Remarks</span></span>

<span data-ttu-id="c2d84-108">Na sintaxe anterior, *tipo de exceção* é o nome de um nova linguagem F# tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gerar uma exceção desse tipo.</span><span class="sxs-lookup"><span data-stu-id="c2d84-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="c2d84-109">Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.</span><span class="sxs-lookup"><span data-stu-id="c2d84-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="c2d84-110">Uma definição típica para uma exceção do F# é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="c2d84-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="c2d84-111">Você pode gerar uma exceção desse tipo usando o `raise` de função, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c2d84-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="c2d84-112">Você pode usar um tipo de exceção do F# diretamente em filtros em um `try...with` expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2d84-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="c2d84-113">O tipo de exceção que você define com as `exception` palavra-chave em F# é um novo tipo que herda de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c2d84-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2d84-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d84-114">See also</span></span>

- [<span data-ttu-id="c2d84-115">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="c2d84-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="c2d84-116">Exceções: a função `raise`</span><span class="sxs-lookup"><span data-stu-id="c2d84-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="c2d84-117">Hierarquia de exceções</span><span class="sxs-lookup"><span data-stu-id="c2d84-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
