---
title: 'Como: chamar um procedimento que retorna um valor (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
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
ms.openlocfilehash: cc1e274a705618213c830d7cf4f61a5e64afd980
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="98671-102">Como chamar um procedimento que retorna um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98671-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="98671-103">Um `Function` procedimento retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="98671-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="98671-104">Você chamá-lo, incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="98671-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="98671-105">Para chamar um procedimento Function em uma expressão</span><span class="sxs-lookup"><span data-stu-id="98671-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="98671-106">Use o `Function` da mesma maneira que você usaria uma variável de nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="98671-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="98671-107">Você pode usar um `Function` chamada de procedimento, você pode usar uma variável ou constante em uma expressão em qualquer lugar.</span><span class="sxs-lookup"><span data-stu-id="98671-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="98671-108">Siga o nome do procedimento com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="98671-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="98671-109">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="98671-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="98671-110">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="98671-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="98671-111">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="98671-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="98671-112">Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="98671-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="98671-113">Como alternativa, você pode passar um ou mais argumentos por nome.</span><span class="sxs-lookup"><span data-stu-id="98671-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="98671-114">Para obter mais informações, consulte [passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="98671-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="98671-115">O valor retornado do procedimento participa na expressão apenas como o valor de uma variável ou constante participaria.</span><span class="sxs-lookup"><span data-stu-id="98671-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="98671-116">Para chamar um procedimento Function em uma instrução de atribuição</span><span class="sxs-lookup"><span data-stu-id="98671-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="98671-117">Use o `Function` nome do procedimento a seguir a igual (`=`) entrar a instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="98671-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="98671-118">Siga o nome do procedimento com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="98671-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="98671-119">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="98671-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="98671-120">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="98671-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="98671-121">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="98671-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="98671-122">Certifique-se de fornecer os argumentos na mesma ordem que a `Function` procedimento define os parâmetros correspondentes, a menos que você esteja passando-os por nome.</span><span class="sxs-lookup"><span data-stu-id="98671-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="98671-123">O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="98671-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98671-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98671-124">Example</span></span>  
 <span data-ttu-id="98671-125">A exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>para recuperar o valor de uma variável de ambiente do sistema operacional.</xref:Microsoft.VisualBasic.Interaction.Environ%2A></span><span class="sxs-lookup"><span data-stu-id="98671-125">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="98671-126">A primeira linha chama `Environ` dentro de uma expressão e a segunda linha chama-o em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="98671-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="98671-127">`Environ`usa o nome da variável como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="98671-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="98671-128">Ele retorna o valor da variável para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="98671-128">It returns the variable's value to the calling code.</span></span>  
  
 <span data-ttu-id="98671-129">[!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="98671-129">[!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98671-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98671-130">See Also</span></span>  
 <span data-ttu-id="98671-131">[Procedimentos de função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="98671-131">[Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="98671-132"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="98671-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="98671-133"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="98671-133"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="98671-134"> [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="98671-134"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="98671-135"> [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="98671-135"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="98671-136"> [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="98671-136"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
