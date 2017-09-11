---
title: 'Como: atribuir uma matriz a outra matriz (Visual Basic) | Documentos do Microsoft'
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
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
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
ms.openlocfilehash: 5732e9dbafb32ff1f12c4586aa4d3e3c2439cc85
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="9dd7e-102">Como atribuir uma matriz a outra matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dd7e-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="9dd7e-103">Como matrizes são objetos, você pode usá-los em instruções de atribuição como outros tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="9dd7e-104">Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de posição e comprimento, e uma atribuição copia somente esse ponteiro.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="9dd7e-105">Para atribuir uma matriz a outra matriz</span><span class="sxs-lookup"><span data-stu-id="9dd7e-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="9dd7e-106">Verifique se as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="9dd7e-107">Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="9dd7e-108">Não siga o nome da matriz com parênteses.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="9dd7e-109">Quando você atribuir uma matriz a outra, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="9dd7e-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="9dd7e-110">**Ordens iguais.**</span><span class="sxs-lookup"><span data-stu-id="9dd7e-110">**Equal Ranks.**</span></span> <span data-ttu-id="9dd7e-111">A classificação (número de dimensões) da matriz de destino deve ser o mesmo que a matriz de origem.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="9dd7e-112">Desde que as classificações de duas matrizes forem iguais, as dimensões não precisam ser iguais.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="9dd7e-113">O número de elementos em uma determinada dimensão pode mudar durante a atribuição.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="9dd7e-114">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="9dd7e-114">**Element Types.**</span></span> <span data-ttu-id="9dd7e-115">A ambas as matrizes devem ter *tipo de referência* elementos ou ambas as matrizes devem ter *tipo de valor* elementos.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="9dd7e-116">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9dd7e-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="9dd7e-117">Se as duas matrizes têm elementos de tipo de valor, os tipos de dados do elemento devem ser exatamente o mesmo.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="9dd7e-118">A única exceção a isso é que você pode atribuir uma matriz de `Enum` elementos em uma matriz do tipo base do que `Enum`.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="9dd7e-119">Se as duas matrizes têm referência a elementos de tipo, o tipo de elemento de origem deve derivar do tipo de elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="9dd7e-120">Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="9dd7e-121">Isso é chamado de *covariância de matriz*.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="9dd7e-122">O compilador relatará um erro se as regras acima são violadas, por exemplo, se os tipos de dados não forem compatíveis ou as classificações são diferentes.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="9dd7e-123">Você pode adicionar tratamento de erros em seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="9dd7e-124">Você também pode usar o [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave se você quiser evitar lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9dd7e-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd7e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dd7e-125">See Also</span></span>  
 <span data-ttu-id="9dd7e-126">[Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="9dd7e-126">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="9dd7e-127"> [Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="9dd7e-127"> [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md) </span></span>  
<span data-ttu-id="9dd7e-128"> [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9dd7e-128"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="9dd7e-129"> [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="9dd7e-129"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)</span></span>
