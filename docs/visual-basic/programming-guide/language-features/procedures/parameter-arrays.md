---
title: Matrizes de parâmetros (Visual Basic)
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
ms.openlocfilehash: 285a5f10e2394fcb001a652fad66e8128b9fbc1a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424611"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="d2411-102">Matrizes de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2411-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="d2411-103">Normalmente, você não pode chamar um procedimento com mais argumentos do que a declaração de procedimento especifica.</span><span class="sxs-lookup"><span data-stu-id="d2411-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="d2411-104">Quando você precisar de um número indefinido de argumentos, poderá declarar uma *matriz de parâmetros*, que permite que um procedimento aceite uma matriz de valores para um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d2411-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="d2411-105">Você não precisa saber o número de elementos na matriz de parâmetros ao definir o procedimento.</span><span class="sxs-lookup"><span data-stu-id="d2411-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="d2411-106">O tamanho da matriz é determinado individualmente por cada chamada para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="d2411-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="d2411-107">Declarando um ParamArray</span><span class="sxs-lookup"><span data-stu-id="d2411-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="d2411-108">Você usa a palavra-chave [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) para denotar uma matriz de parâmetros na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d2411-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="d2411-109">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="d2411-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="d2411-110">Um procedimento pode definir apenas uma matriz de parâmetros e deve ser o último parâmetro na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="d2411-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="d2411-111">A matriz de parâmetros deve ser passada por valor.</span><span class="sxs-lookup"><span data-stu-id="d2411-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="d2411-112">É uma boa prática de programação incluir explicitamente a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="d2411-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="d2411-113">A matriz de parâmetros é opcional automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d2411-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="d2411-114">Seu valor padrão é uma matriz unidimensional vazia do tipo de elemento da matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d2411-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="d2411-115">Todos os parâmetros anteriores à matriz de parâmetros devem ser necessários.</span><span class="sxs-lookup"><span data-stu-id="d2411-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="d2411-116">A matriz de parâmetros deve ser o único parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="d2411-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="d2411-117">Chamando um ParamArray</span><span class="sxs-lookup"><span data-stu-id="d2411-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="d2411-118">Ao chamar um procedimento que define uma matriz de parâmetros, você pode fornecer o argumento de qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d2411-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="d2411-119">Nada — ou seja, você pode omitir o argumento [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) .</span><span class="sxs-lookup"><span data-stu-id="d2411-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="d2411-120">Nesse caso, uma matriz vazia é passada para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="d2411-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="d2411-121">Se você passar explicitamente a palavra-chave [Nothing](../../../../visual-basic/language-reference/nothing.md) , uma matriz NULL será passada para o procedimento e poderá resultar em uma NullReferenceException se o procedimento chamado não verificar essa condição.</span><span class="sxs-lookup"><span data-stu-id="d2411-121">If you explicitly pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="d2411-122">Uma lista de um número arbitrário de argumentos, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d2411-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="d2411-123">O tipo de dados de cada argumento deve ser implicitamente conversível para o tipo de elemento `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="d2411-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="d2411-124">Uma matriz com o mesmo tipo de elemento que o tipo de elemento da matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d2411-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="d2411-125">Em todos os casos, o código dentro do procedimento trata a matriz de parâmetros como uma matriz unidimensional com elementos do mesmo tipo de dados que o tipo de dados `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="d2411-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d2411-126">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2411-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="d2411-127">Se você aceitar uma matriz de parâmetros, deverá testar o tamanho da matriz que o código de chamada passou para ela.</span><span class="sxs-lookup"><span data-stu-id="d2411-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="d2411-128">Siga as etapas apropriadas se for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2411-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="d2411-129">Saiba mais em [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2411-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2411-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2411-130">Example</span></span>  
 <span data-ttu-id="d2411-131">O exemplo a seguir define e chama a função `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="d2411-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="d2411-132">O modificador de `ParamArray` para o parâmetro `args` permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d2411-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="d2411-133">O exemplo a seguir define um procedimento com uma matriz de parâmetros e gera os valores de todos os elementos de matriz passados para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d2411-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="d2411-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2411-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="d2411-135">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="d2411-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d2411-136">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="d2411-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d2411-137">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="d2411-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d2411-138">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="d2411-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="d2411-139">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="d2411-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="d2411-140">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="d2411-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d2411-141">Matrizes</span><span class="sxs-lookup"><span data-stu-id="d2411-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d2411-142">Opcional</span><span class="sxs-lookup"><span data-stu-id="d2411-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
