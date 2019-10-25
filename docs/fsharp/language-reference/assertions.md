---
title: Asserções
description: Saiba como usar a expressão ' Assert ' como um recurso de depuração para testar expressões na linguagem F# de programação.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799068"
---
# <a name="assertions"></a><span data-ttu-id="5ec79-103">Asserções</span><span class="sxs-lookup"><span data-stu-id="5ec79-103">Assertions</span></span>

<span data-ttu-id="5ec79-104">A expressão de `assert` é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5ec79-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="5ec79-105">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="5ec79-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ec79-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ec79-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="5ec79-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ec79-107">Remarks</span></span>

<span data-ttu-id="5ec79-108">A expressão de `assert` tem `bool -> unit`de tipo.</span><span class="sxs-lookup"><span data-stu-id="5ec79-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="5ec79-109">A função `assert` resolve para <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5ec79-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ec79-110">Isso significa que seu comportamento é idêntico a ter chamado <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> diretamente.</span><span class="sxs-lookup"><span data-stu-id="5ec79-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="5ec79-111">A verificação de asserção é habilitada somente quando você compila no modo de depuração; ou seja, se a constante `DEBUG` for definida.</span><span class="sxs-lookup"><span data-stu-id="5ec79-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="5ec79-112">No sistema do projeto, por padrão, a constante `DEBUG` é definida na configuração de depuração, mas não na configuração da versão.</span><span class="sxs-lookup"><span data-stu-id="5ec79-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="5ec79-113">O erro de falha de asserção não pode ser F# capturado usando a manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="5ec79-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="5ec79-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ec79-114">Example</span></span>

<span data-ttu-id="5ec79-115">O exemplo de código a seguir ilustra o uso da expressão `assert`.</span><span class="sxs-lookup"><span data-stu-id="5ec79-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="5ec79-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ec79-116">See also</span></span>

- [<span data-ttu-id="5ec79-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5ec79-117">F# Language Reference</span></span>](index.md)
