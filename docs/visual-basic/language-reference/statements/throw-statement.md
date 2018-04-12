---
title: Instrução Throw (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="95c65-102">Instrução Throw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c65-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="95c65-103">Gera uma exceção dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="95c65-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95c65-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="95c65-105">Parte</span><span class="sxs-lookup"><span data-stu-id="95c65-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="95c65-106">Fornece informações sobre a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="95c65-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="95c65-107">Opcional quando residente em um `Catch` instrução, caso contrário, é necessária.</span><span class="sxs-lookup"><span data-stu-id="95c65-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c65-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="95c65-108">Remarks</span></span>  
 <span data-ttu-id="95c65-109">O `Throw` instrução gera uma exceção que você pode manipular com código de tratamento de exceções estruturado (`Try`... `Catch`... `Finally`) ou código de tratamento de exceção não estruturado (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="95c65-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="95c65-110">Você pode usar o `Throw` instrução para interceptar erros em seu código, pois o Visual Basic move para cima a pilha de chamadas até encontrar o código de tratamento de exceção apropriado.</span><span class="sxs-lookup"><span data-stu-id="95c65-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="95c65-111">Um `Throw` instrução com nenhuma expressão somente pode ser usada em uma `Catch` instrução, em que a instrução lança novamente a exceção atualmente sendo tratada pelo `Catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="95c65-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="95c65-112">O `Throw` instrução redefine a pilha de chamadas para o `expression` exceção.</span><span class="sxs-lookup"><span data-stu-id="95c65-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="95c65-113">Se `expression` não for fornecido, a pilha de chamadas é deixada inalterada.</span><span class="sxs-lookup"><span data-stu-id="95c65-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="95c65-114">Você pode acessar a pilha de chamadas para a exceção por meio de <xref:System.Exception.StackTrace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="95c65-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c65-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95c65-115">Example</span></span>  
 <span data-ttu-id="95c65-116">O código a seguir usa o `Throw` instrução para lançar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="95c65-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="95c65-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95c65-117">Requirements</span></span>  
 <span data-ttu-id="95c65-118">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="95c65-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="95c65-119">**Módulo:**`Interaction`</span><span class="sxs-lookup"><span data-stu-id="95c65-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="95c65-120">**Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="95c65-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c65-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c65-121">See Also</span></span>  
 [<span data-ttu-id="95c65-122">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="95c65-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="95c65-123">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="95c65-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
