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
ms.openlocfilehash: f69ed6e0040f33f810d324a76859d448e9dc7632
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64601136"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="74251-102">Conversões de matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74251-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="74251-103">Você pode converter um tipo de matriz a um tipo de matriz diferente, desde que atendem às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="74251-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="74251-104">**Classificação igual.**</span><span class="sxs-lookup"><span data-stu-id="74251-104">**Equal Rank.**</span></span> <span data-ttu-id="74251-105">As classificações de duas matrizes devem ser as mesmas, ou seja, eles devem ter o mesmo número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="74251-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="74251-106">No entanto, os comprimentos das dimensões respectivos não precisa ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="74251-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="74251-107">**Tipo de dados do elemento.**</span><span class="sxs-lookup"><span data-stu-id="74251-107">**Element Data Type.**</span></span> <span data-ttu-id="74251-108">Os tipos de dados dos elementos de ambas as matrizes devem ser tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="74251-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="74251-109">Não é possível converter um `Integer` de matriz para uma `Long` array ou até mesmo em um `Object` de matriz, pois o tipo de pelo menos um valor está envolvido.</span><span class="sxs-lookup"><span data-stu-id="74251-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="74251-110">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="74251-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="74251-111">**Convertibilidade.**</span><span class="sxs-lookup"><span data-stu-id="74251-111">**Convertibility.**</span></span> <span data-ttu-id="74251-112">Uma conversão de ampliação ou redução, deve ser possível entre os tipos de elementos de duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="74251-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="74251-113">Um exemplo que falha esse requisito é uma tentativa de conversão entre uma `String` matriz e uma matriz de uma classe derivam de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74251-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="74251-114">Esses dois tipos não têm nada em comum, e nenhuma conversão de qualquer tipo existe entre eles.</span><span class="sxs-lookup"><span data-stu-id="74251-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="74251-115">Uma conversão de tipo de uma matriz para outra é de ampliação ou redução dependendo se a conversão dos respectivos elementos é de ampliação ou redução.</span><span class="sxs-lookup"><span data-stu-id="74251-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="74251-116">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="74251-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="74251-117">Conversão em uma matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="74251-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="74251-118">Quando você declara uma `Object` matriz sem inicializá-la, o tipo de elemento é `Object` , desde que ele permaneça não inicializado.</span><span class="sxs-lookup"><span data-stu-id="74251-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="74251-119">Quando você defini-lo para uma matriz de uma classe específica, ele usa o tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="74251-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="74251-120">No entanto, seu tipo subjacente ainda é `Object`, e, posteriormente, você pode defini-lo para outra matriz de uma classe não relacionada.</span><span class="sxs-lookup"><span data-stu-id="74251-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="74251-121">Uma vez que todas as classes derivam `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe para qualquer outra classe.</span><span class="sxs-lookup"><span data-stu-id="74251-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="74251-122">No exemplo a seguir, não existe conversão entre tipos `student` e `String`, mas ambos derivam `Object`, portanto, todas as atribuições são válidas.</span><span class="sxs-lookup"><span data-stu-id="74251-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="74251-123">Tipo subjacente de uma matriz</span><span class="sxs-lookup"><span data-stu-id="74251-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="74251-124">Se você originalmente declarar uma matriz com uma classe específica, seu tipo de elemento subjacente é dessa classe.</span><span class="sxs-lookup"><span data-stu-id="74251-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="74251-125">Se, posteriormente, defini-lo para uma matriz de outra classe, deve haver uma conversão entre as duas classes.</span><span class="sxs-lookup"><span data-stu-id="74251-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="74251-126">No exemplo a seguir `students` é um `student` matriz.</span><span class="sxs-lookup"><span data-stu-id="74251-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="74251-127">Uma vez que não existe conversão entre `String` e `student`, a última instrução falha.</span><span class="sxs-lookup"><span data-stu-id="74251-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="74251-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74251-128">See also</span></span>

- [<span data-ttu-id="74251-129">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="74251-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="74251-130">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74251-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="74251-131">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="74251-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="74251-132">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="74251-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="74251-133">Como: Converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74251-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="74251-134">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="74251-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="74251-135">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="74251-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="74251-136">Matrizes</span><span class="sxs-lookup"><span data-stu-id="74251-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
