---
title: "Instrução throw (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Throw
dev_langs:
- VB
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement, about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement, throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 37f026d09b390214b3f3f2477886f66b1420c591
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="1a90d-102">Instrução Throw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a90d-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="1a90d-103">Lança uma exceção dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="1a90d-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a90d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a90d-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="1a90d-105">Parte</span><span class="sxs-lookup"><span data-stu-id="1a90d-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="1a90d-106">Fornece informações sobre a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="1a90d-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="1a90d-107">Opcional quando residente em uma `Catch` instrução, caso contrário, é necessária.</span><span class="sxs-lookup"><span data-stu-id="1a90d-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a90d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a90d-108">Remarks</span></span>  
 <span data-ttu-id="1a90d-109">O `Throw` instrução gera uma exceção que você pode manipular com código de manipulação de exceção estruturado (`Try`... `Catch`... `Finally`) ou código de manipulação de exceção não estruturado (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="1a90d-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="1a90d-110">Você pode usar o `Throw` instrução para interceptar erros em seu código, pois o Visual Basic move para cima a pilha de chamadas até encontrar o código de manipulação de exceção apropriado.</span><span class="sxs-lookup"><span data-stu-id="1a90d-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="1a90d-111">Um `Throw` instrução com nenhuma expressão somente pode ser usada em uma `Catch` no qual a instrução case Relança a exceção atualmente sendo tratada pela instrução de `Catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="1a90d-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="1a90d-112">O `Throw` instrução redefine a pilha de chamadas para o `expression` exceção.</span><span class="sxs-lookup"><span data-stu-id="1a90d-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="1a90d-113">Se `expression` não for fornecido, a pilha de chamadas é deixada inalterada.</span><span class="sxs-lookup"><span data-stu-id="1a90d-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="1a90d-114">Você pode acessar a pilha de chamadas para a exceção através do <xref:System.Exception.StackTrace%2A>propriedade.</xref:System.Exception.StackTrace%2A></span><span class="sxs-lookup"><span data-stu-id="1a90d-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a90d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a90d-115">Example</span></span>  
 <span data-ttu-id="1a90d-116">O código a seguir usa o `Throw` instrução lançar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="1a90d-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 <span data-ttu-id="1a90d-117">[!code-vb[VbVbalrStatements&#84;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1a90d-117">[!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a90d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a90d-118">Requirements</span></span>  
 <span data-ttu-id="1a90d-119">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="1a90d-119">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="1a90d-120">**Módulo:**`Interaction`</span><span class="sxs-lookup"><span data-stu-id="1a90d-120">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="1a90d-121">**Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="1a90d-121">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a90d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a90d-122">See Also</span></span>  
 <span data-ttu-id="1a90d-123">[Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1a90d-123">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="1a90d-124"> [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)</span><span class="sxs-lookup"><span data-stu-id="1a90d-124"> [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)</span></span>
