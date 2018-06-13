---
title: Instrução Resume
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 1d03f631893be51529f29af824de0d684bf43804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603776"
---
# <a name="resume-statement"></a><span data-ttu-id="844c7-102">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="844c7-102">Resume Statement</span></span>
<span data-ttu-id="844c7-103">Retoma a execução após a conclusão de uma rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="844c7-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="844c7-104">Sugerimos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e `On Error` e `Resume` instruções.</span><span class="sxs-lookup"><span data-stu-id="844c7-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="844c7-105">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="844c7-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="844c7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="844c7-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="844c7-107">Partes</span><span class="sxs-lookup"><span data-stu-id="844c7-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="844c7-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="844c7-108">Required.</span></span> <span data-ttu-id="844c7-109">Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução continua com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="844c7-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="844c7-110">Se o erro ocorreu em um procedimento chamado, retoma a execução na instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="844c7-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="844c7-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="844c7-111">Optional.</span></span> <span data-ttu-id="844c7-112">Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução continua com a instrução imediatamente após a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="844c7-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="844c7-113">Se o erro ocorreu em um procedimento de chamada, a execução continua com a instrução imediatamente após a instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros (ou `On Error Resume Next` instrução).</span><span class="sxs-lookup"><span data-stu-id="844c7-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="844c7-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="844c7-114">Optional.</span></span> <span data-ttu-id="844c7-115">Retoma a execução na linha especificada no necessários `line` argumento.</span><span class="sxs-lookup"><span data-stu-id="844c7-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="844c7-116">O `line` argumento é um rótulo de linha ou um número de linha e deve estar no mesmo procedimento que o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="844c7-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="844c7-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="844c7-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="844c7-118">Recomendamos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e `On Error` e `Resume` instruções.</span><span class="sxs-lookup"><span data-stu-id="844c7-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="844c7-119">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="844c7-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="844c7-120">Se você usar um `Resume` declaração em qualquer lugar diferente em uma rotina de tratamento de erros, um erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="844c7-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="844c7-121">O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="844c7-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="844c7-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="844c7-122">Example</span></span>  
 <span data-ttu-id="844c7-123">Este exemplo usa o `Resume` instrução terminar em um procedimento de tratamento de erros e, em seguida, retomar a execução com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="844c7-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="844c7-124">Número do erro 55 é gerado para ilustrar o uso de `Resume` instrução.</span><span class="sxs-lookup"><span data-stu-id="844c7-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="844c7-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="844c7-125">Requirements</span></span>  
 <span data-ttu-id="844c7-126">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="844c7-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="844c7-127">**Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="844c7-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844c7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="844c7-128">See Also</span></span>  
 [<span data-ttu-id="844c7-129">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="844c7-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="844c7-130">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="844c7-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="844c7-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="844c7-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
