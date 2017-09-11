---
title: "Como: inicializar uma variável de matriz no Visual Basic | Documentos do Microsoft"
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
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: 42
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
ms.openlocfilehash: 5f2bdc8338aadba7f9832603a8ebead49f878e4f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="8dc6b-102">Como inicializar uma variável de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8dc6b-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="8dc6b-103">Você deve inicializar uma variável de matriz, incluindo uma matriz literal em uma `New` cláusula e especificando os valores iniciais da matriz.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="8dc6b-104">Você pode especificar o tipo ou permitir que ele ser inferidos dos valores na matriz de literal.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="8dc6b-105">Para obter mais informações sobre como o tipo é inferido, consulte "Preencher uma matriz com valores iniciais" [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8dc6b-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="8dc6b-106">Para inicializar uma variável de matriz usando um literal de matriz</span><span class="sxs-lookup"><span data-stu-id="8dc6b-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="8dc6b-107">No `New` cláusula, ou quando você atribui o valor de matriz, forneça os valores dos elementos dentro de chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="8dc6b-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="8dc6b-108">O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz com elementos do tipo `Char`.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     <span data-ttu-id="8dc6b-109">[!code-vb[VbVbalrArrays n º&16;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-109">[!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]</span></span>  
  
     <span data-ttu-id="8dc6b-110">Após cada instrução é executada, a matriz que é criada tem um comprimento igual a 3, com elementos no índice 0 até índice 2 que contém os valores iniciais.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-110">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="8dc6b-111">Se você fornecer o limite superior e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-111">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="8dc6b-112">Observe que você não precisa especificar o limite superior do índice se você fornecer valores de elemento em um literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-112">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="8dc6b-113">Se nenhum limite superior for especificado, o tamanho da matriz é inferido com base no número de valores na matriz literal.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-113">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="8dc6b-114">Para inicializar uma variável de matriz multidimensional usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="8dc6b-114">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="8dc6b-115">Aninhar valores entre chaves (`{}`) entre chaves.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-115">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="8dc6b-116">Certifique-se de que os literais de matriz aninhada que todos inferir como matrizes do mesmo tipo e comprimento.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-116">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="8dc6b-117">O exemplo de código a seguir mostra vários exemplos de inicialização de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-117">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     <span data-ttu-id="8dc6b-118">[!code-vb[17 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-118">[!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]</span></span>  
  
-   <span data-ttu-id="8dc6b-119">Explicitamente você pode especificar os limites da matriz, ou omiti-los e que o compilador inferir os limites de matriz com base nos valores do literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-119">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="8dc6b-120">Se você fornecer os limites superiores e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior de cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-120">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="8dc6b-121">O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz bidimensional com elementos do tipo`Short`</span><span class="sxs-lookup"><span data-stu-id="8dc6b-121">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     <span data-ttu-id="8dc6b-122">[!code-vb[VbVbalrArrays n º&18;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-122">[!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]</span></span>  
  
     <span data-ttu-id="8dc6b-123">Após cada instrução é executada, a matriz criada contém seis elementos inicializados com índices `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, e `(1,2)`.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-123">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="8dc6b-124">Cada local da matriz contém o valor `10`.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-124">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="8dc6b-125">O exemplo a seguir itera em uma matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-125">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="8dc6b-126">Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-126">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="8dc6b-127">Os comentários do último mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-127">The last comments show the output.</span></span>  
  
     <span data-ttu-id="8dc6b-128">[!code-vb[VbVbalrArrays&#31;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-128">[!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]</span></span>  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="8dc6b-129">Para inicializar uma variável de matriz denteada usando literais de matriz</span><span class="sxs-lookup"><span data-stu-id="8dc6b-129">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="8dc6b-130">Aninhar valores de objeto entre chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="8dc6b-130">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="8dc6b-131">Embora você também pode aninhar literais de matriz que especificam matrizes de tamanhos diferentes, no caso de uma matriz denteada, certifique-se que os literais de matriz aninhados são colocados entre parênteses (`()`).</span><span class="sxs-lookup"><span data-stu-id="8dc6b-131">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="8dc6b-132">Os parênteses forçam a avaliação dos literais de matriz aninhada e os conjuntos resultantes são usados como os valores iniciais da matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-132">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="8dc6b-133">O exemplo de código a seguir mostra dois exemplos de inicialização de matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-133">The following code example shows two examples of jagged array initialization.</span></span>  
  
     <span data-ttu-id="8dc6b-134">[!code-vb[19 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-134">[!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]</span></span>  
  
-   <span data-ttu-id="8dc6b-135">O exemplo a seguir itera em uma matriz denteada.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-135">The following example iterates through a jagged array.</span></span> <span data-ttu-id="8dc6b-136">Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-136">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="8dc6b-137">Os último comentários no código mostram a saída.</span><span class="sxs-lookup"><span data-stu-id="8dc6b-137">The last comments in the code show the output.</span></span>  
  
     <span data-ttu-id="8dc6b-138">[!code-vb[32 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="8dc6b-138">[!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc6b-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc6b-139">See Also</span></span>  
 <span data-ttu-id="8dc6b-140">[Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dc6b-140">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="8dc6b-141"> [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="8dc6b-141"> [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)</span></span>
