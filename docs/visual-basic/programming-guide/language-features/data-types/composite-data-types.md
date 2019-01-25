---
title: Tipos de dados compostos (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: c7243108d0b7c06f48a21f343321322bb2cc2946
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560276"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="a1e4a-102">Tipos de dados compostos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1e4a-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="a1e4a-103">Além das fontes de Visual Basic de tipos de dados elementar, você também pode montar itens de diferentes tipos para criar *tipos de dados compostos* como classes, matrizes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="a1e4a-104">Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="a1e4a-105">Por exemplo, você pode definir uma matriz de elementos de estrutura, ou uma estrutura com membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a1e4a-106">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a1e4a-106">Data Types</span></span>  
 <span data-ttu-id="a1e4a-107">Um tipo composto é diferente do tipo de dados de qualquer um dos seus componentes.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="a1e4a-108">Por exemplo, uma matriz de `Integer` elementos não é do `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="a1e4a-109">Um tipo de dados de matriz normalmente é representado usando o tipo de elemento, parênteses e vírgulas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="a1e4a-110">Por exemplo, uma matriz unidimensional do `String` elementos é representado como `String()`e uma matriz bidimensional de `Boolean` elementos é representado como `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="a1e4a-111">Tipos de estrutura</span><span class="sxs-lookup"><span data-stu-id="a1e4a-111">Structure Types</span></span>  
 <span data-ttu-id="a1e4a-112">Não há nenhum tipo de dados único que inclui todas as estruturas.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="a1e4a-113">Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo se duas estruturas definem elementos idênticos na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="a1e4a-114">No entanto, se você criar duas ou mais instâncias da mesma estrutura, o Visual Basic considera que eles sejam do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="a1e4a-115">Tuplas</span><span class="sxs-lookup"><span data-stu-id="a1e4a-115">Tuples</span></span>

<span data-ttu-id="a1e4a-116">Uma tupla é uma estrutura leve que contém dois ou mais campos cujos tipos são predefinidos.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="a1e4a-117">As tuplas têm suporte, começando com o Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="a1e4a-118">As tuplas são mais comumente usadas para retornar vários valores de uma única chamada de método sem ter que passar argumentos por referência ou Empacotando os campos retornados em uma classe ou estrutura em mais pesada.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="a1e4a-119">Consulte a [tuplas](tuples.md) tópico para obter mais informações sobre as tuplas.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="a1e4a-120">Tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="a1e4a-120">Array Types</span></span>  
 <span data-ttu-id="a1e4a-121">Não há nenhum tipo de dados único que inclui todas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="a1e4a-122">O tipo de dados de uma instância específica de uma matriz é determinado pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="a1e4a-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="a1e4a-123">O fato de ser uma matriz</span><span class="sxs-lookup"><span data-stu-id="a1e4a-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="a1e4a-124">A classificação (número de dimensões) da matriz</span><span class="sxs-lookup"><span data-stu-id="a1e4a-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="a1e4a-125">O tipo de elemento da matriz</span><span class="sxs-lookup"><span data-stu-id="a1e4a-125">The element type of the array</span></span>  
  
 <span data-ttu-id="a1e4a-126">Em particular, o comprimento de uma determinada dimensão não é parte da instância tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="a1e4a-127">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="a1e4a-128">No exemplo anterior, as variáveis de matriz `arrayA` e `arrayB` são considerados para ser do mesmo tipo de dados — `Byte()` — mesmo que eles são inicializados para diferentes comprimentos.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="a1e4a-129">Variáveis `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elemento são diferentes.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="a1e4a-130">Variáveis `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="a1e4a-131">Variáveis `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e os tipos de elemento são os mesmos, embora `arrayD` ainda não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="a1e4a-132">Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1e4a-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="a1e4a-133">Tipos de classe</span><span class="sxs-lookup"><span data-stu-id="a1e4a-133">Class Types</span></span>  
 <span data-ttu-id="a1e4a-134">Não há nenhum tipo de dados único que inclui todas as classes.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="a1e4a-135">Embora uma classe pode herdar de outra classe, cada um é um tipo de dados separado.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="a1e4a-136">Várias instâncias da mesma classe são do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="a1e4a-137">Se você atribuir uma variável de instância de classe para outra, não apenas têm os mesmos dados de tipo, eles apontam para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="a1e4a-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="a1e4a-138">Para obter mais informações sobre classes, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1e4a-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e4a-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1e4a-139">See also</span></span>
- [<span data-ttu-id="a1e4a-140">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a1e4a-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a1e4a-141">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="a1e4a-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="a1e4a-142">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1e4a-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a1e4a-143">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="a1e4a-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="a1e4a-144">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1e4a-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="a1e4a-145">Estruturas</span><span class="sxs-lookup"><span data-stu-id="a1e4a-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a1e4a-146">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a1e4a-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="a1e4a-147">Como: manter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="a1e4a-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
