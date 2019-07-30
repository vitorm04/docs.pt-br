---
title: Tipos de exceção
description: Saiba como definir e usar F# tipos de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630315"
---
# <a name="exception-types"></a><span data-ttu-id="693f9-103">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="693f9-103">Exception Types</span></span>

<span data-ttu-id="693f9-104">Há duas categorias de exceções no: F#tipos de exceção do .NET F# e tipos de exceção.</span><span class="sxs-lookup"><span data-stu-id="693f9-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="693f9-105">Este tópico descreve como definir e usar F# tipos de exceção.</span><span class="sxs-lookup"><span data-stu-id="693f9-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="693f9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="693f9-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="693f9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="693f9-107">Remarks</span></span>

<span data-ttu-id="693f9-108">Na sintaxe anterior, o *tipo de exceção* é o nome de um novo F# tipo de exceção, e o *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gera uma exceção desse tipo.</span><span class="sxs-lookup"><span data-stu-id="693f9-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="693f9-109">Você pode especificar vários argumentos usando um tipo de tupla para o *tipo de argumento*.</span><span class="sxs-lookup"><span data-stu-id="693f9-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="693f9-110">Uma definição típica para uma F# exceção é semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="693f9-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="693f9-111">Você pode gerar uma exceção desse tipo usando a função, `raise` da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="693f9-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="693f9-112">Você pode usar um F# tipo de exceção diretamente nos filtros em uma `try...with` expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="693f9-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="693f9-113">O tipo de exceção que você define com `exception` a palavra F# -chave in é um novo tipo `System.Exception`que herda de.</span><span class="sxs-lookup"><span data-stu-id="693f9-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="693f9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="693f9-114">See also</span></span>

- [<span data-ttu-id="693f9-115">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="693f9-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="693f9-116">Exceções: a função `raise`</span><span class="sxs-lookup"><span data-stu-id="693f9-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="693f9-117">Hierarquia de exceções</span><span class="sxs-lookup"><span data-stu-id="693f9-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
