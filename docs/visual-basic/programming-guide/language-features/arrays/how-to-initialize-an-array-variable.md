---
title: "Como inicializar uma variável de matriz no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="4a349-102">Como inicializar uma variável de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a349-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="4a349-103">Inicializar uma variável de matriz, incluindo uma matriz literal em uma `New` cláusula e especificando os valores iniciais da matriz.</span><span class="sxs-lookup"><span data-stu-id="4a349-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="4a349-104">Você pode especificar o tipo ou permitir que ele ser deduzido dos valores na matriz literal.</span><span class="sxs-lookup"><span data-stu-id="4a349-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="4a349-105">Para obter mais informações sobre como o tipo é inferido, consulte "Preencher uma matriz com valores iniciais" [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a349-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="4a349-106">Para inicializar uma variável de matriz usando um literal de matriz</span><span class="sxs-lookup"><span data-stu-id="4a349-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="4a349-107">No `New` cláusula, ou quando você atribui o valor de matriz, forneça os valores de elemento entre chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="4a349-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="4a349-108">O exemplo a seguir mostra várias maneiras para declarar e criar e inicializar uma variável para conter uma matriz com os elementos do tipo `Char`.</span><span class="sxs-lookup"><span data-stu-id="4a349-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="4a349-109">Depois de cada instrução é executada, a matriz que é criada tem um comprimento de 3, com elementos no índice 0 até índice 2 que contém os valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="4a349-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="4a349-110">Se você fornecer o limite superior e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior.</span><span class="sxs-lookup"><span data-stu-id="4a349-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="4a349-111">Observe que você não precisa especificar o limite superior do índice se você fornecer valores de elemento em um literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="4a349-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="4a349-112">Se nenhum limite superior é especificado, o tamanho da matriz é inferido com base no número de valores na matriz literal.</span><span class="sxs-lookup"><span data-stu-id="4a349-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="4a349-113">Para inicializar uma variável de matriz multidimensional usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="4a349-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="4a349-114">Aninhar valores entre chaves (`{}`) entre chaves.</span><span class="sxs-lookup"><span data-stu-id="4a349-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="4a349-115">Certifique-se de que os literais de matriz aninhada que todos inferir como matrizes do mesmo tipo e comprimento.</span><span class="sxs-lookup"><span data-stu-id="4a349-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="4a349-116">O exemplo de código a seguir mostra vários exemplos de inicialização de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="4a349-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="4a349-117">Explicitamente especifique os limites da matriz, ou omita e que o compilador inferir os limites de matriz com base nos valores de literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="4a349-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="4a349-118">Se você fornecer os limites superiores e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior de cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="4a349-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="4a349-119">O exemplo a seguir mostra várias maneiras para declarar e criar e inicializar uma variável para conter uma matriz bidimensional com elementos do tipo`Short`</span><span class="sxs-lookup"><span data-stu-id="4a349-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="4a349-120">Depois de cada instrução é executada, a matriz criada contém seis inicializados elementos que têm índices `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, e `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="4a349-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="4a349-121">Cada local de matriz contém o valor `10`.</span><span class="sxs-lookup"><span data-stu-id="4a349-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="4a349-122">O exemplo a seguir itera por meio de uma matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="4a349-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="4a349-123">Em um aplicativo de console do Windows que está escrito em Visual Basic, cole o código dentro de `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="4a349-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="4a349-124">Os comentários a última mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="4a349-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="4a349-125">Para inicializar uma variável de matriz denteada usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="4a349-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="4a349-126">Aninhar valores de objeto entre chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="4a349-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="4a349-127">Embora você também pode aninhar literais de matriz que especificam matrizes de tamanhos diferentes, no caso de uma matriz denteada, certifique-se de que os literais de matriz aninhada estão entre parênteses (`()`).</span><span class="sxs-lookup"><span data-stu-id="4a349-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="4a349-128">Os parênteses forçam a avaliação dos literais de matriz aninhada, e os conjuntos resultantes são usados como os valores iniciais da matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="4a349-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="4a349-129">O exemplo de código a seguir mostra dois exemplos de inicialização de matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="4a349-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="4a349-130">O exemplo a seguir itera por meio de uma matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="4a349-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="4a349-131">Em um aplicativo de console do Windows que está escrito em Visual Basic, cole o código dentro de `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="4a349-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="4a349-132">Os último comentários no código mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="4a349-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a349-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a349-133">See Also</span></span>  
 [<span data-ttu-id="4a349-134">Matrizes</span><span class="sxs-lookup"><span data-stu-id="4a349-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="4a349-135">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="4a349-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
