---
title: Asserções
description: Saiba como usar a expressão ' Assert ' como um recurso de depuração para testar expressões na linguagem F# de programação.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630031"
---
# <a name="assertions"></a><span data-ttu-id="ca520-103">Asserções</span><span class="sxs-lookup"><span data-stu-id="ca520-103">Assertions</span></span>

<span data-ttu-id="ca520-104">A `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ca520-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="ca520-105">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="ca520-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca520-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca520-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="ca520-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca520-107">Remarks</span></span>

<span data-ttu-id="ca520-108">A `assert` expressão tem o `bool -> unit`tipo.</span><span class="sxs-lookup"><span data-stu-id="ca520-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="ca520-109">Na sintaxe anterior, *Condition* representa uma expressão booliana a ser testada.</span><span class="sxs-lookup"><span data-stu-id="ca520-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="ca520-110">Se a expressão for avaliada `true`como, a execução continuará inalterada.</span><span class="sxs-lookup"><span data-stu-id="ca520-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="ca520-111">Se ele for avaliado como `false`, uma caixa de diálogo de erro do sistema será gerada.</span><span class="sxs-lookup"><span data-stu-id="ca520-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="ca520-112">A caixa de diálogo de erro tem uma legenda que contém a declaração de cadeia de caracteres **com falha**.</span><span class="sxs-lookup"><span data-stu-id="ca520-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="ca520-113">A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.</span><span class="sxs-lookup"><span data-stu-id="ca520-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="ca520-114">A verificação de asserção é habilitada somente quando você compila no modo de depuração; ou seja, se a constante `DEBUG` for definida.</span><span class="sxs-lookup"><span data-stu-id="ca520-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="ca520-115">No sistema do projeto, por padrão, a `DEBUG` constante é definida na configuração de depuração, mas não na configuração da versão.</span><span class="sxs-lookup"><span data-stu-id="ca520-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="ca520-116">O erro de falha de asserção não pode ser F# capturado usando a manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="ca520-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="ca520-117">A `assert` função é resolvida para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca520-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ca520-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca520-118">Example</span></span>

<span data-ttu-id="ca520-119">O exemplo de código a seguir ilustra o uso `assert` da expressão.</span><span class="sxs-lookup"><span data-stu-id="ca520-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="ca520-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca520-120">See also</span></span>

- [<span data-ttu-id="ca520-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="ca520-121">F# Language Reference</span></span>](index.md)
