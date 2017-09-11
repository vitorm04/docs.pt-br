---
title: "Matrizes de parâmetros (Visual Basic) | Documentos do Microsoft"
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
- parameter arrays, about parameter arrays
- ParamArray keyword, parameter arrays
- Visual Basic code, procedures
- parameters, parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures, indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: 26
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
ms.openlocfilehash: 3ac0662e281dce21d92e08cbaffd313dc701ee5c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="dd260-102">Matrizes de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd260-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="dd260-103">Normalmente, você não pode chamar um procedimento com mais argumentos do que especifica a declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="dd260-104">Quando você precisar de um número indefinido de argumentos, você pode declarar uma *matriz de parâmetros*, que permite que um procedimento aceitar uma matriz de valores para um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dd260-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="dd260-105">Você não precisa saber o número de elementos na matriz de parâmetros quando você define o procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="dd260-106">O tamanho da matriz é determinado individualmente por cada chamada ao procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="dd260-107">Declarando um ParamArray</span><span class="sxs-lookup"><span data-stu-id="dd260-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="dd260-108">Você usa o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) palavra-chave para denotar uma matriz de parâmetros na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dd260-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="dd260-109">As seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="dd260-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="dd260-110">Um procedimento pode definir apenas uma matriz de parâmetros, e ele deve ser o último parâmetro na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="dd260-111">A matriz de parâmetros deve ser passada por valor.</span><span class="sxs-lookup"><span data-stu-id="dd260-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="dd260-112">É uma boa prática para incluir explicitamente de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) palavra-chave na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="dd260-113">A matriz de parâmetros é automaticamente opcional.</span><span class="sxs-lookup"><span data-stu-id="dd260-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="dd260-114">O valor padrão é uma matriz unidimensional vazia do tipo de elemento da matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dd260-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="dd260-115">Todos os parâmetros que precedem a matriz de parâmetros devem ser necessários.</span><span class="sxs-lookup"><span data-stu-id="dd260-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="dd260-116">A matriz de parâmetros deve ser o único parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="dd260-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="dd260-117">Chamando um ParamArray</span><span class="sxs-lookup"><span data-stu-id="dd260-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="dd260-118">Quando você chama um procedimento que define uma matriz de parâmetros, você pode fornecer o argumento em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="dd260-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="dd260-119">Nada — ou seja, você pode omitir o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumento.</span><span class="sxs-lookup"><span data-stu-id="dd260-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="dd260-120">Nesse caso, uma matriz vazia é passada para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd260-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="dd260-121">Você também pode passar o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, com o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="dd260-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="dd260-122">Uma lista de um número arbitrário de argumentos, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="dd260-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="dd260-123">O tipo de dados de cada argumento deve ser implicitamente conversível para o `ParamArray` tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="dd260-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="dd260-124">Uma matriz com o mesmo tipo de elemento do tipo de elemento da matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dd260-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="dd260-125">Em todos os casos, o código dentro do procedimento trata a matriz de parâmetros como uma matriz unidimensional com elementos do mesmo tipo de dados como o `ParamArray` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="dd260-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd260-126">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd260-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="dd260-127">Se você aceitar uma matriz de parâmetros, você deve testar o tamanho da matriz que o código de chamada passado para ele.</span><span class="sxs-lookup"><span data-stu-id="dd260-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="dd260-128">Execute as etapas apropriadas se ele for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd260-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="dd260-129">Para obter mais informações, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd260-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd260-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd260-130">Example</span></span>  
 <span data-ttu-id="dd260-131">O exemplo a seguir define e chama a função `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="dd260-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="dd260-132">O `ParamArray` modificador para o parâmetro `args` permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="dd260-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 <span data-ttu-id="dd260-133">[!code-vb[VbVbalrStatements&#26;](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="dd260-133">[!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]</span></span>  
  
 <span data-ttu-id="dd260-134">O exemplo a seguir define um procedimento com uma matriz de parâmetros e retorna os valores de todos os elementos da matriz passados à matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="dd260-134">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 <span data-ttu-id="dd260-135">[!code-vb[48 VbVbcnProcedures](./codesnippet/VisualBasic/parameter-arrays_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="dd260-135">[!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]</span></span>  
  
 <span data-ttu-id="dd260-136">[!code-vb[49 VbVbcnProcedures](./codesnippet/VisualBasic/parameter-arrays_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="dd260-136">[!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd260-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd260-137">See Also</span></span>  
 <span data-ttu-id="dd260-138"><xref:Microsoft.VisualBasic.Information.UBound%2A></xref:Microsoft.VisualBasic.Information.UBound%2A></span><span class="sxs-lookup"><span data-stu-id="dd260-138"><xref:Microsoft.VisualBasic.Information.UBound%2A></span></span>   
<span data-ttu-id="dd260-139"> [Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-139"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="dd260-140"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-140"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="dd260-141"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-141"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="dd260-142"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-142"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="dd260-143"> [Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-143"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="dd260-144"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-144"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="dd260-145"> [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd260-145"> [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="dd260-146"> [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)</span><span class="sxs-lookup"><span data-stu-id="dd260-146"> [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)</span></span>
