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
ms.openlocfilehash: db9d47798d087d60f4318b06fe3291fb895e6618
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871870"
---
# <a name="resume-statement"></a><span data-ttu-id="081dc-102">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="081dc-102">Resume Statement</span></span>

<span data-ttu-id="081dc-103">Retoma a execução após a conclusão de uma rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="081dc-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="081dc-104">Sugerimos que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as `On Error` `Resume` instruções e.</span><span class="sxs-lookup"><span data-stu-id="081dc-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="081dc-105">Para obter mais informações, consulte [Instrução Try...Catch...Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="081dc-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="081dc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="081dc-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="081dc-107">Partes</span><span class="sxs-lookup"><span data-stu-id="081dc-107">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="081dc-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="081dc-108">Required.</span></span> <span data-ttu-id="081dc-109">Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="081dc-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="081dc-110">Se o erro ocorreu em um procedimento chamado, a execução será retomada na instrução última chamada para fora do procedimento que contém a rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="081dc-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="081dc-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="081dc-111">Optional.</span></span> <span data-ttu-id="081dc-112">Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução imediatamente após a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="081dc-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="081dc-113">Se o erro ocorreu em um procedimento chamado, a execução será retomada com a instrução imediatamente após a instrução que a última chamada para fora do procedimento que contém a rotina de tratamento de erros (ou a `On Error Resume Next` instrução).</span><span class="sxs-lookup"><span data-stu-id="081dc-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="081dc-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="081dc-114">Optional.</span></span> <span data-ttu-id="081dc-115">A execução é retomada na linha especificada no `line` argumento necessário.</span><span class="sxs-lookup"><span data-stu-id="081dc-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="081dc-116">O `line` argumento é um rótulo de linha ou número de linha e deve estar no mesmo procedimento que o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="081dc-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="081dc-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="081dc-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="081dc-118">É recomendável que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as `On Error` `Resume` instruções e.</span><span class="sxs-lookup"><span data-stu-id="081dc-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="081dc-119">Para obter mais informações, consulte [Instrução Try...Catch...Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="081dc-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="081dc-120">Se você usar uma `Resume` instrução em qualquer lugar que não seja em uma rotina de tratamento de erros, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="081dc-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="081dc-121">A `Resume` instrução não pode ser usada em nenhum procedimento que contenha uma `Try...Catch...Finally` instrução.</span><span class="sxs-lookup"><span data-stu-id="081dc-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="081dc-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="081dc-122">Example</span></span>  

 <span data-ttu-id="081dc-123">Este exemplo usa a `Resume` instrução para encerrar o tratamento de erros em um procedimento e, em seguida, retomar a execução com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="081dc-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="081dc-124">O número de erro 55 é gerado para ilustrar o uso da `Resume` instrução.</span><span class="sxs-lookup"><span data-stu-id="081dc-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="081dc-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="081dc-125">Requirements</span></span>  

 <span data-ttu-id="081dc-126">**Namespace:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="081dc-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="081dc-127">**Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="081dc-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081dc-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="081dc-128">See also</span></span>

- [<span data-ttu-id="081dc-129">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="081dc-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="081dc-130">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="081dc-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="081dc-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="081dc-131">On Error Statement</span></span>](on-error-statement.md)
