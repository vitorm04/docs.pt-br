---
title: Matrizes de parâmetros
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: ffb532fbac70b9aa8ab210450e4d9207f5e0291f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351119"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="65db9-102">Matrizes de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65db9-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="65db9-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span><span class="sxs-lookup"><span data-stu-id="65db9-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="65db9-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span><span class="sxs-lookup"><span data-stu-id="65db9-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="65db9-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span><span class="sxs-lookup"><span data-stu-id="65db9-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="65db9-106">The array size is determined individually by each call to the procedure.</span><span class="sxs-lookup"><span data-stu-id="65db9-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="65db9-107">Declaring a ParamArray</span><span class="sxs-lookup"><span data-stu-id="65db9-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="65db9-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span><span class="sxs-lookup"><span data-stu-id="65db9-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="65db9-109">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="65db9-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="65db9-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span><span class="sxs-lookup"><span data-stu-id="65db9-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="65db9-111">The parameter array must be passed by value.</span><span class="sxs-lookup"><span data-stu-id="65db9-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="65db9-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span><span class="sxs-lookup"><span data-stu-id="65db9-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="65db9-113">The parameter array is automatically optional.</span><span class="sxs-lookup"><span data-stu-id="65db9-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="65db9-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span><span class="sxs-lookup"><span data-stu-id="65db9-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="65db9-115">All parameters preceding the parameter array must be required.</span><span class="sxs-lookup"><span data-stu-id="65db9-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="65db9-116">The parameter array must be the only optional parameter.</span><span class="sxs-lookup"><span data-stu-id="65db9-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="65db9-117">Calling a ParamArray</span><span class="sxs-lookup"><span data-stu-id="65db9-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="65db9-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span><span class="sxs-lookup"><span data-stu-id="65db9-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="65db9-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span><span class="sxs-lookup"><span data-stu-id="65db9-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="65db9-120">In this case, an empty array is passed to the procedure.</span><span class="sxs-lookup"><span data-stu-id="65db9-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="65db9-121">If you explicitly pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span><span class="sxs-lookup"><span data-stu-id="65db9-121">If you explicitly pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="65db9-122">A list of an arbitrary number of arguments, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="65db9-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="65db9-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span><span class="sxs-lookup"><span data-stu-id="65db9-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="65db9-124">An array with the same element type as the parameter array's element type.</span><span class="sxs-lookup"><span data-stu-id="65db9-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="65db9-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span><span class="sxs-lookup"><span data-stu-id="65db9-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="65db9-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span><span class="sxs-lookup"><span data-stu-id="65db9-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="65db9-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span><span class="sxs-lookup"><span data-stu-id="65db9-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="65db9-128">Take appropriate steps if it is too large for your application.</span><span class="sxs-lookup"><span data-stu-id="65db9-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="65db9-129">Saiba mais em [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="65db9-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65db9-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65db9-130">Example</span></span>  
 <span data-ttu-id="65db9-131">The following example defines and calls the function `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="65db9-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="65db9-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span><span class="sxs-lookup"><span data-stu-id="65db9-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="65db9-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span><span class="sxs-lookup"><span data-stu-id="65db9-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="65db9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65db9-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="65db9-135">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="65db9-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="65db9-136">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="65db9-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="65db9-137">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="65db9-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="65db9-138">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="65db9-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="65db9-139">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="65db9-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="65db9-140">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="65db9-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="65db9-141">Matrizes</span><span class="sxs-lookup"><span data-stu-id="65db9-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="65db9-142">Opcional</span><span class="sxs-lookup"><span data-stu-id="65db9-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
