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
ms.openlocfilehash: 768559c7a6caf064f7529786675e51ce19667d6b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581710"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="d5f0c-102">Tipos de dados compostos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5f0c-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="d5f0c-103">Além dos tipos de dados elementares Visual Basic suprimentos, você também pode montar itens de tipos diferentes para criar *tipos de dados compostos* , como estruturas, matrizes e classes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="d5f0c-104">Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="d5f0c-105">Por exemplo, você pode definir uma matriz de elementos de estrutura ou uma estrutura com membros de matriz.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="d5f0c-106">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="d5f0c-106">Data Types</span></span>  
 <span data-ttu-id="d5f0c-107">Um tipo composto é diferente do tipo de dados de qualquer um de seus componentes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="d5f0c-108">Por exemplo, uma matriz de elementos de `Integer` não é do tipo de dados `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="d5f0c-109">Um tipo de dados de matriz normalmente é representado usando o tipo de elemento, parênteses e vírgulas, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="d5f0c-110">Por exemplo, uma matriz unidimensional de elementos `String` é representada como `String()` e uma matriz bidimensional de elementos `Boolean` é representada como `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="d5f0c-111">Tipos de estrutura</span><span class="sxs-lookup"><span data-stu-id="d5f0c-111">Structure Types</span></span>  
 <span data-ttu-id="d5f0c-112">Não há nenhum tipo de dados único composto por todas as estruturas.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="d5f0c-113">Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo que duas estruturas definam elementos idênticos na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="d5f0c-114">No entanto, se você criar duas ou mais instâncias da mesma estrutura, Visual Basic as considerará como sendo do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="d5f0c-115">Tuplas</span><span class="sxs-lookup"><span data-stu-id="d5f0c-115">Tuples</span></span>

<span data-ttu-id="d5f0c-116">Uma tupla é uma estrutura leve que contém dois ou mais campos cujos tipos são predefinidos.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="d5f0c-117">As tuplas têm suporte a partir do Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="d5f0c-118">As tuplas são usadas com mais frequência para retornar vários valores de uma única chamada de método sem precisar passar argumentos por referência ou empacotamento dos campos retornados em uma classe ou estrutura mais pesada.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="d5f0c-119">Consulte o tópico [tuplas](tuples.md) para obter mais informações sobre tuplas.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="d5f0c-120">Tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="d5f0c-120">Array Types</span></span>  
 <span data-ttu-id="d5f0c-121">Não há nenhum tipo de dados único composto por todas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="d5f0c-122">O tipo de dados de uma determinada instância de uma matriz é determinado pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5f0c-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="d5f0c-123">O fato de ser uma matriz</span><span class="sxs-lookup"><span data-stu-id="d5f0c-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="d5f0c-124">A classificação (número de dimensões) da matriz</span><span class="sxs-lookup"><span data-stu-id="d5f0c-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="d5f0c-125">O tipo de elemento da matriz</span><span class="sxs-lookup"><span data-stu-id="d5f0c-125">The element type of the array</span></span>  
  
 <span data-ttu-id="d5f0c-126">Em particular, o comprimento de uma determinada dimensão não faz parte do tipo de dados da instância.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="d5f0c-127">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="d5f0c-128">No exemplo anterior, as variáveis de matriz `arrayA` e `arrayB` são consideradas do mesmo tipo de dados — `Byte()` — mesmo que elas sejam inicializadas para diferentes comprimentos.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="d5f0c-129">As variáveis `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elementos são diferentes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="d5f0c-130">As variáveis `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="d5f0c-131">As variáveis `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e os tipos de elementos são os mesmos, mesmo que `arrayD` ainda não tenha sido inicializado.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="d5f0c-132">Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5f0c-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="d5f0c-133">Tipos de classe</span><span class="sxs-lookup"><span data-stu-id="d5f0c-133">Class Types</span></span>  
 <span data-ttu-id="d5f0c-134">Não há nenhum tipo de dados único que abranja todas as classes.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="d5f0c-135">Embora uma classe possa herdar de outra classe, cada uma é um tipo de dados separado.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="d5f0c-136">Várias instâncias da mesma classe são do mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="d5f0c-137">Se você atribuir uma variável de instância de classe a outra, não apenas elas terão o mesmo tipo de dados, elas apontarão para a mesma instância de classe na memória.</span><span class="sxs-lookup"><span data-stu-id="d5f0c-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="d5f0c-138">Para obter mais informações sobre classes, consulte [objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5f0c-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f0c-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5f0c-139">See also</span></span>

- [<span data-ttu-id="d5f0c-140">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="d5f0c-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="d5f0c-141">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="d5f0c-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="d5f0c-142">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5f0c-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d5f0c-143">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="d5f0c-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="d5f0c-144">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5f0c-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="d5f0c-145">Estruturas</span><span class="sxs-lookup"><span data-stu-id="d5f0c-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="d5f0c-146">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="d5f0c-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="d5f0c-147">Como manter mais de um valor em uma variável</span><span class="sxs-lookup"><span data-stu-id="d5f0c-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
