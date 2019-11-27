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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333023"
---
# <a name="resume-statement"></a><span data-ttu-id="d0841-102">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="d0841-102">Resume Statement</span></span>
<span data-ttu-id="d0841-103">Retoma a execução após a conclusão de uma rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="d0841-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="d0841-104">Sugerimos que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as instruções `On Error` e `Resume`.</span><span class="sxs-lookup"><span data-stu-id="d0841-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="d0841-105">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d0841-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0841-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0841-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d0841-107">Partes</span><span class="sxs-lookup"><span data-stu-id="d0841-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="d0841-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d0841-108">Required.</span></span> <span data-ttu-id="d0841-109">Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="d0841-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="d0841-110">Se o erro ocorreu em um procedimento chamado, a execução será retomada na instrução última chamada para fora do procedimento que contém a rotina de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="d0841-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="d0841-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d0841-111">Optional.</span></span> <span data-ttu-id="d0841-112">Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução imediatamente após a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="d0841-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="d0841-113">Se o erro ocorreu em um procedimento chamado, a execução será retomada com a instrução imediatamente após a instrução que a última chamada para fora do procedimento que contém a rotina de tratamento de erros (ou a instrução `On Error Resume Next`).</span><span class="sxs-lookup"><span data-stu-id="d0841-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="d0841-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d0841-114">Optional.</span></span> <span data-ttu-id="d0841-115">A execução é retomada na linha especificada no argumento obrigatório `line`.</span><span class="sxs-lookup"><span data-stu-id="d0841-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="d0841-116">O argumento `line` é um rótulo de linha ou número de linha e deve estar no mesmo procedimento que o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="d0841-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0841-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0841-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0841-118">É recomendável que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as instruções `On Error` e `Resume`.</span><span class="sxs-lookup"><span data-stu-id="d0841-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="d0841-119">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d0841-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="d0841-120">Se você usar uma instrução `Resume` em qualquer lugar diferente de em uma rotina de tratamento de erros, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="d0841-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="d0841-121">A instrução `Resume` não pode ser usada em nenhum procedimento que contenha uma instrução `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="d0841-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0841-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0841-122">Example</span></span>  
 <span data-ttu-id="d0841-123">Este exemplo usa a instrução `Resume` para encerrar o tratamento de erros em um procedimento e, em seguida, retomar a execução com a instrução que causou o erro.</span><span class="sxs-lookup"><span data-stu-id="d0841-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="d0841-124">O número de erro 55 é gerado para ilustrar o uso da instrução `Resume`.</span><span class="sxs-lookup"><span data-stu-id="d0841-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="d0841-125">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d0841-125">Requirements</span></span>  
 <span data-ttu-id="d0841-126">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="d0841-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="d0841-127">**Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="d0841-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0841-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0841-128">See also</span></span>

- [<span data-ttu-id="d0841-129">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="d0841-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="d0841-130">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="d0841-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="d0841-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="d0841-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
