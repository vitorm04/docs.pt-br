---
title: "Asserções (F#)"
description: "Saiba como usar a expressão 'assert' como um recurso de depuração para testar expressões em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a><span data-ttu-id="bb86d-104">Asserções</span><span class="sxs-lookup"><span data-stu-id="bb86d-104">Assertions</span></span>

<span data-ttu-id="bb86d-105">O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="bb86d-105">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="bb86d-106">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="bb86d-106">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb86d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb86d-107">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="bb86d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb86d-108">Remarks</span></span>

<span data-ttu-id="bb86d-109">O `assert` expressão tem tipo `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="bb86d-109">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="bb86d-110">Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado.</span><span class="sxs-lookup"><span data-stu-id="bb86d-110">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="bb86d-111">Se a expressão for avaliada como `true`, a execução continua afetados.</span><span class="sxs-lookup"><span data-stu-id="bb86d-111">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="bb86d-112">Se ele for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada.</span><span class="sxs-lookup"><span data-stu-id="bb86d-112">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="bb86d-113">A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **falha de asserção**.</span><span class="sxs-lookup"><span data-stu-id="bb86d-113">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="bb86d-114">A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.</span><span class="sxs-lookup"><span data-stu-id="bb86d-114">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="bb86d-115">A verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` está definido.</span><span class="sxs-lookup"><span data-stu-id="bb86d-115">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="bb86d-116">No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na versão de configuração.</span><span class="sxs-lookup"><span data-stu-id="bb86d-116">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="bb86d-117">O erro de falha de asserção não pode ser capturado por meio de tratamento de exceção F #.</span><span class="sxs-lookup"><span data-stu-id="bb86d-117">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="bb86d-118">O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb86d-118">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="bb86d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb86d-119">Example</span></span>

<span data-ttu-id="bb86d-120">O exemplo de código a seguir ilustra o uso do `assert` expressão.</span><span class="sxs-lookup"><span data-stu-id="bb86d-120">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="bb86d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb86d-121">See Also</span></span>

[<span data-ttu-id="bb86d-122">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="bb86d-122">F# Language Reference</span></span>](index.md)
