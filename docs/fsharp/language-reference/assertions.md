---
title: Asserções (F#)
description: "Saiba como usar a expressão 'Declare' como um recurso de depuração para testar expressões na linguagem de programação F #."
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000169"
---
# <a name="assertions"></a><span data-ttu-id="ad4a0-103">Asserções</span><span class="sxs-lookup"><span data-stu-id="ad4a0-103">Assertions</span></span>

<span data-ttu-id="ad4a0-104">O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="ad4a0-105">Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad4a0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad4a0-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="ad4a0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad4a0-107">Remarks</span></span>

<span data-ttu-id="ad4a0-108">O `assert` expressão tem o tipo `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="ad4a0-109">Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="ad4a0-110">Se a expressão for avaliada como `true`, a execução continua sem ser afetada.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="ad4a0-111">Se for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="ad4a0-112">A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **Falha na asserção**.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="ad4a0-113">A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="ad4a0-114">Verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` é definido.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="ad4a0-115">No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na configuração de versão.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="ad4a0-116">O erro de falha de asserção não pode ser detectado por meio de manipulação de exceção do F #.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="ad4a0-117">O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ad4a0-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad4a0-118">Example</span></span>

<span data-ttu-id="ad4a0-119">O exemplo de código a seguir ilustra o uso do `assert` expressão.</span><span class="sxs-lookup"><span data-stu-id="ad4a0-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="ad4a0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad4a0-120">See also</span></span>

- [<span data-ttu-id="ad4a0-121">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="ad4a0-121">F# Language Reference</span></span>](index.md)
