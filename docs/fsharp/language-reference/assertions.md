---
title: Asserções (F#)
description: Saiba como usar a expressão 'Declare' como um recurso de depuração para testar expressões no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: fbaf038f08cfc74e6cb262c110322dc586813c0c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127245"
---
# <a name="assertions"></a><span data-ttu-id="bab24-103">Asserções</span><span class="sxs-lookup"><span data-stu-id="bab24-103">Assertions</span></span>

<span data-ttu-id="bab24-104">O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="bab24-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="bab24-105">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="bab24-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="bab24-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bab24-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="bab24-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bab24-107">Remarks</span></span>

<span data-ttu-id="bab24-108">O `assert` expressão tem o tipo `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="bab24-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="bab24-109">Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado.</span><span class="sxs-lookup"><span data-stu-id="bab24-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="bab24-110">Se a expressão for avaliada como `true`, a execução continua sem ser afetada.</span><span class="sxs-lookup"><span data-stu-id="bab24-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="bab24-111">Se for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada.</span><span class="sxs-lookup"><span data-stu-id="bab24-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="bab24-112">A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **Falha na asserção**.</span><span class="sxs-lookup"><span data-stu-id="bab24-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="bab24-113">A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.</span><span class="sxs-lookup"><span data-stu-id="bab24-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="bab24-114">Verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` é definido.</span><span class="sxs-lookup"><span data-stu-id="bab24-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="bab24-115">No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na configuração de versão.</span><span class="sxs-lookup"><span data-stu-id="bab24-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="bab24-116">O erro de falha de asserção não pode ser capturado usando F# tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="bab24-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="bab24-117">O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bab24-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="bab24-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab24-118">Example</span></span>

<span data-ttu-id="bab24-119">O exemplo de código a seguir ilustra o uso do `assert` expressão.</span><span class="sxs-lookup"><span data-stu-id="bab24-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="bab24-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bab24-120">See also</span></span>

- [<span data-ttu-id="bab24-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="bab24-121">F# Language Reference</span></span>](index.md)
