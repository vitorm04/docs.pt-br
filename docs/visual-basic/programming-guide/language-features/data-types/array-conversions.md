---
title: "Matriz conversões (Visual Basic) | Documentos do Microsoft"
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
- arrays [Visual Basic], converting type
- type conversion, arrays
- conversions, type
- arrays [Visual Basic], data types
- conversions, data type
- object arrays, converting type
- data type conversion, array conversions
- conversions, array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: 14
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
ms.openlocfilehash: be6c806d80a68b50a58936903ced15e4287a7b51
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="7a5c1-102">Conversões de matriz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a5c1-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="7a5c1-103">Você pode converter um tipo de matriz a um tipo de matriz diferente, desde que atendem às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="7a5c1-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="7a5c1-104">**Classificação igual.**</span><span class="sxs-lookup"><span data-stu-id="7a5c1-104">**Equal Rank.**</span></span> <span data-ttu-id="7a5c1-105">As classificações de duas matrizes devem ser as mesmas, ou seja, eles devem ter o mesmo número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="7a5c1-106">No entanto, os comprimentos das respectivas dimensões não precisa ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="7a5c1-107">**Tipo de dados do elemento.**</span><span class="sxs-lookup"><span data-stu-id="7a5c1-107">**Element Data Type.**</span></span> <span data-ttu-id="7a5c1-108">Os tipos de dados dos elementos de ambas as matrizes devem ser tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="7a5c1-109">Não é possível converter um `Integer` de matriz para uma `Long` de matriz, ou mesmo um `Object` de matriz, pois o tipo de pelo menos um valor está envolvido.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="7a5c1-110">Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c1-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="7a5c1-111">**Convertibilidade.**</span><span class="sxs-lookup"><span data-stu-id="7a5c1-111">**Convertibility.**</span></span> <span data-ttu-id="7a5c1-112">Uma conversão de ampliação ou redução, deve ser possível entre os tipos de elemento das duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="7a5c1-113">Um exemplo que falha esse requisito é uma tentativa de conversão entre uma `String` matriz e uma matriz de uma classe derivam de <xref:System.Attribute?displayProperty=fullName>.</xref:System.Attribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7a5c1-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=fullName>.</span></span> <span data-ttu-id="7a5c1-114">Esses dois tipos não têm nada em comum e nenhuma conversão de qualquer tipo existe entre eles.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="7a5c1-115">Uma conversão de tipo de uma matriz para outro é ampliação ou redução dependendo se a conversão dos respectivos elementos é de ampliação ou redução.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="7a5c1-116">Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c1-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="7a5c1-117">Conversão em uma matriz de objetos</span><span class="sxs-lookup"><span data-stu-id="7a5c1-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="7a5c1-118">Ao declarar uma `Object` matriz sem inicializá-la, seu tipo de elemento é `Object` enquanto ele permanece não inicializado.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="7a5c1-119">Quando você defini-la para uma matriz de uma classe específica, ele usa o tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="7a5c1-120">No entanto, seu tipo subjacente ainda é `Object`, e você pode defini-lo posteriormente a outra matriz de uma classe não relacionada.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="7a5c1-121">Como todas as classes derivam `Object`, você pode alterar o tipo de elemento da matriz de qualquer classe a qualquer outra classe.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="7a5c1-122">No exemplo a seguir, não existe nenhuma conversão entre tipos `student` e `String`, mas ambos derivam `Object`, portanto, todas as atribuições são válidas.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="7a5c1-123">Tipo subjacente de uma matriz</span><span class="sxs-lookup"><span data-stu-id="7a5c1-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="7a5c1-124">Se você originalmente declarar uma matriz com uma classe específica, seu tipo subjacente do elemento é dessa classe.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="7a5c1-125">Se você subsequentemente configurá-lo para uma matriz de outra classe, deve haver uma conversão entre as duas classes.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="7a5c1-126">No exemplo a seguir, `students` é um `student` matriz.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="7a5c1-127">Como nenhuma conversão existe entre `String` e `student`, a última instrução falha.</span><span class="sxs-lookup"><span data-stu-id="7a5c1-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a5c1-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a5c1-128">See Also</span></span>  
 <span data-ttu-id="7a5c1-129">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-129">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="7a5c1-130"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-130"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="7a5c1-131"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-131"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="7a5c1-132"> [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-132"> [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span></span>  
<span data-ttu-id="7a5c1-133"> [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-133"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="7a5c1-134"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-134"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="7a5c1-135"> [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="7a5c1-135"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="7a5c1-136"> [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)</span><span class="sxs-lookup"><span data-stu-id="7a5c1-136"> [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md)</span></span>
