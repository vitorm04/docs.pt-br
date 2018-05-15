---
title: Como atribuir uma matriz a outra matriz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="27793-102">Como atribuir uma matriz a outra matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27793-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="27793-103">Como matrizes são objetos, você pode usá-los em instruções de atribuição como outros tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="27793-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="27793-104">Uma variável de matriz contém um ponteiro para os dados que constituem os elementos da matriz e as informações de classificação e comprimento, e uma atribuição copia somente esse ponteiro.</span><span class="sxs-lookup"><span data-stu-id="27793-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="27793-105">Para atribuir uma matriz a outra matriz</span><span class="sxs-lookup"><span data-stu-id="27793-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="27793-106">Certifique-se de que as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.</span><span class="sxs-lookup"><span data-stu-id="27793-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="27793-107">Use uma instrução de atribuição padrão para atribuir a matriz de origem para a matriz de destino.</span><span class="sxs-lookup"><span data-stu-id="27793-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="27793-108">Não execute o nome da matriz com parênteses.</span><span class="sxs-lookup"><span data-stu-id="27793-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="27793-109">Quando você atribui uma matriz para outro, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="27793-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="27793-110">**Ordens iguais.**</span><span class="sxs-lookup"><span data-stu-id="27793-110">**Equal Ranks.**</span></span> <span data-ttu-id="27793-111">A classificação (número de dimensões) da matriz de destino deve ser a mesma que a matriz de origem.</span><span class="sxs-lookup"><span data-stu-id="27793-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="27793-112">Desde que as classificações de duas matrizes forem iguais, as dimensões não precisam ser iguais.</span><span class="sxs-lookup"><span data-stu-id="27793-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="27793-113">O número de elementos em uma determinada dimensão pode mudar durante a atribuição.</span><span class="sxs-lookup"><span data-stu-id="27793-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="27793-114">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="27793-114">**Element Types.**</span></span> <span data-ttu-id="27793-115">Ou ambas as matrizes devem ter *fazem referência a tipo* elementos ou ambas as matrizes devem ter *tipo de valor* elementos.</span><span class="sxs-lookup"><span data-stu-id="27793-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="27793-116">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="27793-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="27793-117">Se as duas matrizes têm elementos de tipo de valor, os tipos de dados do elemento devem ser exatamente os mesmos.</span><span class="sxs-lookup"><span data-stu-id="27793-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="27793-118">A única exceção a isso é que você pode atribuir uma matriz de `Enum` elementos em uma matriz do tipo base do que `Enum`.</span><span class="sxs-lookup"><span data-stu-id="27793-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="27793-119">Se as duas matrizes têm referência a elementos de tipo, o tipo de elemento de origem deve derivar do tipo de elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="27793-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="27793-120">Quando esse for o caso, as duas matrizes têm a mesma relação de herança que seus elementos.</span><span class="sxs-lookup"><span data-stu-id="27793-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="27793-121">Isso é chamado de *covariância*.</span><span class="sxs-lookup"><span data-stu-id="27793-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="27793-122">O compilador relata um erro se as regras acima forem violadas, por exemplo, se os tipos de dados não são compatíveis ou as classificações são diferentes.</span><span class="sxs-lookup"><span data-stu-id="27793-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="27793-123">Você pode adicionar ao seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição de tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="27793-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="27793-124">Você também pode usar o [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave se você quiser evitar lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="27793-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27793-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27793-125">See Also</span></span>  
 [<span data-ttu-id="27793-126">Matrizes</span><span class="sxs-lookup"><span data-stu-id="27793-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="27793-127">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="27793-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="27793-128">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="27793-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="27793-129">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="27793-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
