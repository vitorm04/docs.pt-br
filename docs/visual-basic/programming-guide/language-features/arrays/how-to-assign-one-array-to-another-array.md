---
title: Como atribuir uma matriz a outra matriz
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351886"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="6bb77-102">Como atribuir uma matriz a outra matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bb77-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="6bb77-103">Como as matrizes são objetos, você pode usá-las em instruções de atribuição como outros tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="6bb77-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="6bb77-104">Uma variável de matriz contém um ponteiro para os dados que constituem os elementos de matriz e as informações de classificação e comprimento, e uma atribuição copia apenas esse ponteiro.</span><span class="sxs-lookup"><span data-stu-id="6bb77-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="6bb77-105">Para atribuir uma matriz a outra matriz</span><span class="sxs-lookup"><span data-stu-id="6bb77-105">To assign one array to another array</span></span>

1. <span data-ttu-id="6bb77-106">Verifique se as duas matrizes têm a mesma classificação (número de dimensões) e tipos de dados de elemento compatíveis.</span><span class="sxs-lookup"><span data-stu-id="6bb77-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="6bb77-107">Use uma instrução de atribuição padrão para atribuir a matriz de origem à matriz de destino.</span><span class="sxs-lookup"><span data-stu-id="6bb77-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="6bb77-108">Não siga o nome da matriz com parênteses.</span><span class="sxs-lookup"><span data-stu-id="6bb77-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="6bb77-109">Quando você atribui uma matriz a outra, as seguintes regras se aplicam:</span><span class="sxs-lookup"><span data-stu-id="6bb77-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="6bb77-110">**Classificações iguais.**</span><span class="sxs-lookup"><span data-stu-id="6bb77-110">**Equal Ranks.**</span></span> <span data-ttu-id="6bb77-111">A classificação (número de dimensões) da matriz de destino deve ser a mesma da matriz de origem.</span><span class="sxs-lookup"><span data-stu-id="6bb77-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="6bb77-112">Desde que as classificações das duas matrizes sejam iguais, as dimensões não precisam ser iguais.</span><span class="sxs-lookup"><span data-stu-id="6bb77-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="6bb77-113">O número de elementos em uma determinada dimensão pode ser alterado durante a atribuição.</span><span class="sxs-lookup"><span data-stu-id="6bb77-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="6bb77-114">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="6bb77-114">**Element Types.**</span></span> <span data-ttu-id="6bb77-115">Ambas as matrizes devem ter elementos de *tipo de referência* ou ambas as matrizes devem ter elementos de *tipo de valor* .</span><span class="sxs-lookup"><span data-stu-id="6bb77-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="6bb77-116">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="6bb77-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="6bb77-117">Se ambas as matrizes tiverem elementos de tipo de valor, os tipos de dados de elemento deverão ser exatamente iguais.</span><span class="sxs-lookup"><span data-stu-id="6bb77-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="6bb77-118">A única exceção é que você pode atribuir uma matriz de elementos de `Enum` a uma matriz do tipo base do `Enum`.</span><span class="sxs-lookup"><span data-stu-id="6bb77-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="6bb77-119">Se ambas as matrizes tiverem elementos de tipo de referência, o tipo de elemento de origem deverá derivar do tipo de elemento de destino.</span><span class="sxs-lookup"><span data-stu-id="6bb77-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="6bb77-120">Quando esse for o caso, as duas matrizes terão a mesma relação de herança que seus elementos.</span><span class="sxs-lookup"><span data-stu-id="6bb77-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="6bb77-121">Isso é chamado de *covariância de matriz*.</span><span class="sxs-lookup"><span data-stu-id="6bb77-121">This is called *array covariance*.</span></span>

<span data-ttu-id="6bb77-122">O compilador relatará um erro se as regras acima forem violadas, por exemplo, se os tipos de dados não forem compatíveis ou se as classificações forem desiguais.</span><span class="sxs-lookup"><span data-stu-id="6bb77-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="6bb77-123">Você pode adicionar tratamento de erros ao seu código para certificar-se de que as matrizes são compatíveis antes de tentar uma atribuição.</span><span class="sxs-lookup"><span data-stu-id="6bb77-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="6bb77-124">Você também pode usar a palavra-chave do [Operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) se quiser evitar lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6bb77-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bb77-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bb77-125">See also</span></span>

- [<span data-ttu-id="6bb77-126">Matrizes</span><span class="sxs-lookup"><span data-stu-id="6bb77-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="6bb77-127">Solução de problemas de matrizes</span><span class="sxs-lookup"><span data-stu-id="6bb77-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="6bb77-128">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="6bb77-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="6bb77-129">Conversões de Matriz</span><span class="sxs-lookup"><span data-stu-id="6bb77-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
