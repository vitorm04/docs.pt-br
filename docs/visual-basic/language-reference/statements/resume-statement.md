---
title: "Instrução Resume | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
dev_langs:
- VB
helpviewer_keywords:
- Next statement, Resume
- Resume Next statement
- execution, resuming
- run-time errors, resuming after
- Resume statement, syntax
- errors [Visual Basic], resuming after
- Error statement, and Resume statement
- execution
- Resume statement
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
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
ms.openlocfilehash: 5a0c42d4d884e976f65db68f8417b3678ec000bc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="resume-statement"></a><span data-ttu-id="396d4-102">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="396d4-102">Resume Statement</span></span>
<span data-ttu-id="396d4-103">Retoma a execução após a conclusão de uma rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="396d4-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="396d4-104">Sugerimos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturado e o `On Error` e `Resume` instruções.</span><span class="sxs-lookup"><span data-stu-id="396d4-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="396d4-105">Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="396d4-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396d4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="396d4-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="396d4-107">Partes</span><span class="sxs-lookup"><span data-stu-id="396d4-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="396d4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="396d4-108">Required.</span></span> <span data-ttu-id="396d4-109">Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="396d4-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="396d4-110">Se o erro ocorreu em um procedimento chamado, a execução é retomada na instrução de última chamada do procedimento que contém a rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="396d4-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="396d4-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="396d4-111">Optional.</span></span> <span data-ttu-id="396d4-112">Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução imediatamente após a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="396d4-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="396d4-113">Se o erro ocorreu em um procedimento chamado, a execução continua com a instrução imediatamente após a instrução que a última chamada do procedimento que contém a rotina de tratamento de erros (ou `On Error Resume Next` instrução).</span><span class="sxs-lookup"><span data-stu-id="396d4-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="396d4-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="396d4-114">Optional.</span></span> <span data-ttu-id="396d4-115">A execução é retomada na linha especificada conforme exigido `line` argumento.</span><span class="sxs-lookup"><span data-stu-id="396d4-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="396d4-116">O `line` argumento é um número da linha ou rótulo da linha e deve estar no mesmo procedimento que o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="396d4-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="396d4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="396d4-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="396d4-118">É recomendável que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturado e o `On Error` e `Resume` instruções.</span><span class="sxs-lookup"><span data-stu-id="396d4-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="396d4-119">Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="396d4-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="396d4-120">Se você usar um `Resume` declaração em qualquer local diferente em uma rotina de tratamento de erros, um erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="396d4-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="396d4-121">O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="396d4-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="396d4-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="396d4-122">Example</span></span>  
 <span data-ttu-id="396d4-123">Este exemplo usa o `Resume` instrução para terminar em um procedimento de tratamento de erros e, em seguida, continuar a execução com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="396d4-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="396d4-124">Número do erro 55 é gerado para ilustrar o uso do `Resume` instrução.</span><span class="sxs-lookup"><span data-stu-id="396d4-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 <span data-ttu-id="396d4-125">[!code-vb[VbVbalrErrorHandling n º&16;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="396d4-125">[!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="396d4-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="396d4-126">Requirements</span></span>  
 <span data-ttu-id="396d4-127">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="396d4-127">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="396d4-128">**Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="396d4-128">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396d4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="396d4-129">See Also</span></span>  
 <span data-ttu-id="396d4-130">[Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="396d4-130">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="396d4-131"> [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md) </span><span class="sxs-lookup"><span data-stu-id="396d4-131"> [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md) </span></span>  
<span data-ttu-id="396d4-132"> [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)</span><span class="sxs-lookup"><span data-stu-id="396d4-132"> [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)</span></span>
