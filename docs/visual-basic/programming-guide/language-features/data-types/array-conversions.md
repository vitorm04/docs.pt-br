---
title: Conversões de matriz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581857"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="81310-102">Conversões de matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81310-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="81310-103">Você pode converter um tipo de matriz em um tipo de matriz diferente, desde que atenda às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="81310-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="81310-104">**Classificação igual.**</span><span class="sxs-lookup"><span data-stu-id="81310-104">**Equal Rank.**</span></span> <span data-ttu-id="81310-105">As classificações das duas matrizes devem ser as mesmas, ou seja, devem ter o mesmo número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="81310-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="81310-106">No entanto, os comprimentos das respectivas dimensões não precisam ser os mesmos.</span><span class="sxs-lookup"><span data-stu-id="81310-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="81310-107">**Tipo de dados do elemento.**</span><span class="sxs-lookup"><span data-stu-id="81310-107">**Element Data Type.**</span></span> <span data-ttu-id="81310-108">Os tipos de dados dos elementos de ambas as matrizes devem ser tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="81310-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="81310-109">Não é possível converter uma matriz de `Integer` em uma matriz de `Long` ou até mesmo em uma matriz de `Object`, porque pelo menos um tipo de valor está envolvido.</span><span class="sxs-lookup"><span data-stu-id="81310-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="81310-110">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="81310-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="81310-111">**Convertibilidade.**</span><span class="sxs-lookup"><span data-stu-id="81310-111">**Convertibility.**</span></span> <span data-ttu-id="81310-112">Uma conversão, que pode ser ampliada ou estreita, deve ser possível entre os tipos de elemento das duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="81310-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="81310-113">Um exemplo que falha esse requisito é uma tentativa de conversão entre uma matriz de `String` e uma matriz de uma classe derivada de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81310-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81310-114">Esses dois tipos não têm nada em comum, e não existe nenhuma conversão de nenhum tipo entre eles.</span><span class="sxs-lookup"><span data-stu-id="81310-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="81310-115">Uma conversão de um tipo de matriz para outro está ampliando ou estreitando dependendo se a conversão dos respectivos elementos está ampliando ou diminuindo.</span><span class="sxs-lookup"><span data-stu-id="81310-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="81310-116">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="81310-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="81310-117">Conversão para uma matriz de objeto</span><span class="sxs-lookup"><span data-stu-id="81310-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="81310-118">Quando você declara uma matriz de `Object` sem inicializá-la, seu tipo de elemento é `Object` desde que permaneça não inicializado.</span><span class="sxs-lookup"><span data-stu-id="81310-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="81310-119">Quando você o define como uma matriz de uma classe específica, ela assume o tipo dessa classe.</span><span class="sxs-lookup"><span data-stu-id="81310-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="81310-120">No entanto, seu tipo subjacente ainda é `Object`, e você pode defini-lo posteriormente como outra matriz de uma classe não relacionada.</span><span class="sxs-lookup"><span data-stu-id="81310-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="81310-121">Como todas as classes derivam de `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe para qualquer outra classe.</span><span class="sxs-lookup"><span data-stu-id="81310-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="81310-122">No exemplo a seguir, não existe nenhuma conversão entre os tipos `student` e `String`, mas ambos derivam de `Object`, portanto, todas as atribuições são válidas.</span><span class="sxs-lookup"><span data-stu-id="81310-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="81310-123">Tipo subjacente de uma matriz</span><span class="sxs-lookup"><span data-stu-id="81310-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="81310-124">Se você declarar originalmente uma matriz com uma classe específica, seu tipo de elemento subjacente será essa classe.</span><span class="sxs-lookup"><span data-stu-id="81310-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="81310-125">Se você defini-lo subsequentemente como uma matriz de outra classe, deverá haver uma conversão entre as duas classes.</span><span class="sxs-lookup"><span data-stu-id="81310-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="81310-126">No exemplo a seguir, `students` é uma matriz `student`.</span><span class="sxs-lookup"><span data-stu-id="81310-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="81310-127">Como não existe nenhuma conversão entre `String` e `student`, a última instrução falhará.</span><span class="sxs-lookup"><span data-stu-id="81310-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="81310-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81310-128">See also</span></span>

- [<span data-ttu-id="81310-129">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="81310-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="81310-130">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81310-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="81310-131">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="81310-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="81310-132">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="81310-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="81310-133">Como converter um objeto em outro tipo em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81310-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="81310-134">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="81310-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="81310-135">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="81310-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="81310-136">Matrizes</span><span class="sxs-lookup"><span data-stu-id="81310-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
