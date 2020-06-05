---
title: Como chamar um procedimento que retorna um valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388758"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="37f20-102">Como chamar um procedimento que retorna um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37f20-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="37f20-103">Um `Function` procedimento retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="37f20-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="37f20-104">Você pode chamá-lo incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="37f20-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="37f20-105">Para chamar um procedimento Function dentro de uma expressão</span><span class="sxs-lookup"><span data-stu-id="37f20-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="37f20-106">Use o `Function` nome do procedimento da mesma maneira que usaria uma variável.</span><span class="sxs-lookup"><span data-stu-id="37f20-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="37f20-107">Você pode usar uma `Function` chamada de procedimento em qualquer lugar em que você possa usar uma variável ou constante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="37f20-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="37f20-108">Siga o nome do procedimento com parênteses para colocar a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="37f20-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="37f20-109">Se não houver argumentos, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="37f20-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="37f20-110">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="37f20-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="37f20-111">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="37f20-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="37f20-112">Certifique-se de fornecer os argumentos na mesma ordem em que o `Function` procedimento define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="37f20-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="37f20-113">Como alternativa, você pode passar um ou mais argumentos por nome.</span><span class="sxs-lookup"><span data-stu-id="37f20-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="37f20-114">Para obter mais informações, consulte [passando argumentos por posição e por nome](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="37f20-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="37f20-115">O valor retornado do procedimento participa da expressão da mesma forma que o valor de uma variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="37f20-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="37f20-116">Para chamar um procedimento Function em uma instrução de atribuição</span><span class="sxs-lookup"><span data-stu-id="37f20-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="37f20-117">Use o `Function` nome do procedimento após o sinal de igual ( `=` ) na instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="37f20-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="37f20-118">Siga o nome do procedimento com parênteses para colocar a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="37f20-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="37f20-119">Se não houver argumentos, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="37f20-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="37f20-120">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="37f20-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="37f20-121">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="37f20-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="37f20-122">Certifique-se de fornecer os argumentos na mesma ordem em que o `Function` procedimento define os parâmetros correspondentes, a menos que você os esteja passando por nome.</span><span class="sxs-lookup"><span data-stu-id="37f20-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="37f20-123">O valor retornado do procedimento é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="37f20-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37f20-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37f20-124">Example</span></span>  
 <span data-ttu-id="37f20-125">O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> para recuperar o valor de uma variável de ambiente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="37f20-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="37f20-126">A primeira linha `Environ` é chamada dentro de uma expressão e a segunda linha a chama em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="37f20-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="37f20-127">`Environ`usa o nome da variável como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="37f20-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="37f20-128">Ele retorna o valor da variável para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="37f20-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="37f20-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="37f20-129">See also</span></span>

- [<span data-ttu-id="37f20-130">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="37f20-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="37f20-131">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="37f20-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="37f20-132">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="37f20-132">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="37f20-133">Como criar um procedimento que retorne um valor</span><span class="sxs-lookup"><span data-stu-id="37f20-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="37f20-134">Como retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="37f20-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="37f20-135">Como chamar um procedimento que não retorne um valor</span><span class="sxs-lookup"><span data-stu-id="37f20-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
