---
title: Asserções (F#)
description: "Saiba como usar a expressão 'assert' como um recurso de depuração para testar expressões em F # linguagem de programação."
ms.date: 05/16/2016
ms.openlocfilehash: 83e6cd77bbbb2c32e9b778e5bf6dd9d2e9c8fe32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="assertions"></a><span data-ttu-id="3aa7c-103">Asserções</span><span class="sxs-lookup"><span data-stu-id="3aa7c-103">Assertions</span></span>

<span data-ttu-id="3aa7c-104">O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="3aa7c-105">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="3aa7c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3aa7c-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="3aa7c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3aa7c-107">Remarks</span></span>

<span data-ttu-id="3aa7c-108">O `assert` expressão tem tipo `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="3aa7c-109">Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="3aa7c-110">Se a expressão for avaliada como `true`, a execução continua afetados.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="3aa7c-111">Se ele for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="3aa7c-112">A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **falha de asserção**.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="3aa7c-113">A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="3aa7c-114">A verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` está definido.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="3aa7c-115">No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na versão de configuração.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="3aa7c-116">O erro de falha de asserção não pode ser capturado por meio de tratamento de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="3aa7c-117">O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3aa7c-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3aa7c-118">Example</span></span>

<span data-ttu-id="3aa7c-119">O exemplo de código a seguir ilustra o uso do `assert` expressão.</span><span class="sxs-lookup"><span data-stu-id="3aa7c-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3aa7c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aa7c-120">See Also</span></span>

[<span data-ttu-id="3aa7c-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="3aa7c-121">F# Language Reference</span></span>](index.md)
