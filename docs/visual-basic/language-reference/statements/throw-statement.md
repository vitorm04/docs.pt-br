---
title: Instrução Throw
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352790"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="292dc-102">Instrução Throw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="292dc-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="292dc-103">Gera uma exceção em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="292dc-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="292dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="292dc-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="292dc-105">Parte</span><span class="sxs-lookup"><span data-stu-id="292dc-105">Part</span></span>

`expression`\
<span data-ttu-id="292dc-106">Fornece informações sobre a exceção a ser gerada.</span><span class="sxs-lookup"><span data-stu-id="292dc-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="292dc-107">Opcional ao residir em uma instrução `Catch`, caso contrário, é necessário.</span><span class="sxs-lookup"><span data-stu-id="292dc-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="292dc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="292dc-108">Remarks</span></span>

<span data-ttu-id="292dc-109">A instrução `Throw` gera uma exceção que você pode manipular com código de manipulação de exceção estruturado (`Try`...`Catch`...`Finally`) ou código de tratamento de exceção não estruturado (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="292dc-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="292dc-110">Você pode usar a instrução `Throw` para interceptar erros em seu código porque Visual Basic move para cima a pilha de chamadas até encontrar o código de tratamento de exceção apropriado.</span><span class="sxs-lookup"><span data-stu-id="292dc-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="292dc-111">Uma instrução `Throw` sem expressão só pode ser usada em uma instrução `Catch`; nesse caso, a instrução gera novamente a exceção que está sendo manipulada pela instrução `Catch`.</span><span class="sxs-lookup"><span data-stu-id="292dc-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="292dc-112">A instrução `Throw` redefine a pilha de chamadas para a exceção `expression`.</span><span class="sxs-lookup"><span data-stu-id="292dc-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="292dc-113">Se `expression` não for fornecido, a pilha de chamadas permanecerá inalterada.</span><span class="sxs-lookup"><span data-stu-id="292dc-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="292dc-114">Você pode acessar a pilha de chamadas para a exceção por meio da propriedade <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="292dc-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="292dc-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="292dc-115">Example</span></span>

<span data-ttu-id="292dc-116">O código a seguir usa a instrução `Throw` para gerar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="292dc-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="292dc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="292dc-117">See also</span></span>

- [<span data-ttu-id="292dc-118">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="292dc-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="292dc-119">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="292dc-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
