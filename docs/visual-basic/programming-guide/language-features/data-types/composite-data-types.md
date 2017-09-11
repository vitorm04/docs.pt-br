---
title: Tipos de dados compostos (Visual Basic) | Documentos do Microsoft
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
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
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
ms.openlocfilehash: 5f0c6215ce45d724a7b5c8c4f8e34ea27bce8fe4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="9c6ab-102">Tipos de dados compostos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c6ab-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="9c6ab-103">Além dos tipos de dados elementares [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fontes, você também pode montar itens de diferentes tipos para criar *tipos de dados compostos* como classes, matrizes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-103">In addition to the elementary data types [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="9c6ab-104">Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="9c6ab-105">Por exemplo, você pode definir uma matriz de elementos de estrutura, ou uma estrutura com membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9c6ab-106">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="9c6ab-106">Data Types</span></span>  
 <span data-ttu-id="9c6ab-107">Um tipo composto é diferente do tipo de dados de qualquer um de seus componentes.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="9c6ab-108">Por exemplo, uma matriz de `Integer` elementos não tem o `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="9c6ab-109">Um tipo de dados array é normalmente representado usando o tipo de elemento, parênteses e vírgulas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="9c6ab-110">Por exemplo, uma matriz unidimensional de `String` elementos é representado como `String()`e uma matriz bidimensional de `Boolean` elementos é representado como `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="9c6ab-111">Tipos de estrutura</span><span class="sxs-lookup"><span data-stu-id="9c6ab-111">Structure Types</span></span>  
 <span data-ttu-id="9c6ab-112">Não há nenhum tipo de dados único contendo todas as estruturas.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="9c6ab-113">Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo se duas estruturas definem elementos idênticos na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="9c6ab-114">No entanto, se você criar duas ou mais instâncias da mesma estrutura, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considera ser do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="array-types"></a><span data-ttu-id="9c6ab-115">Tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="9c6ab-115">Array Types</span></span>  
 <span data-ttu-id="9c6ab-116">Não há nenhum tipo de dados único contendo todas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-116">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="9c6ab-117">O tipo de dados de uma instância específica de uma matriz é determinado pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c6ab-117">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="9c6ab-118">O fato de ser uma matriz</span><span class="sxs-lookup"><span data-stu-id="9c6ab-118">The fact of being an array</span></span>  
  
-   <span data-ttu-id="9c6ab-119">A classificação (número de dimensões) da matriz</span><span class="sxs-lookup"><span data-stu-id="9c6ab-119">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="9c6ab-120">O tipo de elemento da matriz</span><span class="sxs-lookup"><span data-stu-id="9c6ab-120">The element type of the array</span></span>  
  
 <span data-ttu-id="9c6ab-121">Em particular, o comprimento de uma determinada dimensão não é parte da instância tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-121">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="9c6ab-122">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-122">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="9c6ab-123">No exemplo anterior, as variáveis array `arrayA` e `arrayB` são considerados para ser do mesmo tipo de dados — `Byte()` — mesmo que eles sejam inicializados para diferentes comprimentos.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-123">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="9c6ab-124">Variáveis de `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elemento são diferentes.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-124">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="9c6ab-125">Variáveis de `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-125">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="9c6ab-126">Variáveis de `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e tipos de elemento são os mesmos, embora `arrayD` ainda não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-126">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="9c6ab-127">Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c6ab-127">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="9c6ab-128">Tipos de classe</span><span class="sxs-lookup"><span data-stu-id="9c6ab-128">Class Types</span></span>  
 <span data-ttu-id="9c6ab-129">Não há nenhum tipo de dados único contendo todas as classes.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-129">There is no single data type comprising all classes.</span></span> <span data-ttu-id="9c6ab-130">Embora uma classe pode herdar de outra classe, cada um é um tipo de dados separado.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-130">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="9c6ab-131">Várias instâncias da mesma classe são do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-131">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="9c6ab-132">Se você atribuir uma variável de instância de classe para outra, não apenas eles têm os mesmos dados de tipo, eles apontam para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-132">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="9c6ab-133">Para obter mais informações sobre classes, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c6ab-133">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6ab-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c6ab-134">See Also</span></span>  
 <span data-ttu-id="9c6ab-135">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-135">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="9c6ab-136"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-136"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="9c6ab-137"> [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-137"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="9c6ab-138"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-138"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="9c6ab-139"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-139"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="9c6ab-140"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-140"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="9c6ab-141"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9c6ab-141"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="9c6ab-142"> [Como manter mais de um valor em uma variável](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span><span class="sxs-lookup"><span data-stu-id="9c6ab-142"> [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span></span>
