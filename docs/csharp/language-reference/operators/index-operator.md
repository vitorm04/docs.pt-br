---
title: "Operador [] (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b49d41af0dd4dc34b1b74c62ce8779aa31d69f77
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="768a7-102">Operador [] (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="768a7-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="768a7-103">Os colchetes (`[]`) são usados para matrizes, indexadores e atributos.</span><span class="sxs-lookup"><span data-stu-id="768a7-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="768a7-104">Eles também podem ser usados com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="768a7-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="768a7-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="768a7-105">Remarks</span></span>  
 <span data-ttu-id="768a7-106">Um tipo de matriz é um tipo seguido por `[]`:</span><span class="sxs-lookup"><span data-stu-id="768a7-106">An array type is a type followed by `[]`:</span></span>  
  
 <span data-ttu-id="768a7-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="768a7-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="768a7-108">Para acessar um elemento de uma matriz, o índice do elemento desejado é colocado entre colchetes:</span><span class="sxs-lookup"><span data-stu-id="768a7-108">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 <span data-ttu-id="768a7-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="768a7-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="768a7-110">Uma exceção será lançada se um índice de matriz estiver fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="768a7-110">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="768a7-111">O operador de indexação da matriz não pode ser sobrecarregado. No entanto, os tipos podem definir indexadores e propriedades que recebem um ou mais parâmetros.</span><span class="sxs-lookup"><span data-stu-id="768a7-111">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="768a7-112">Os parâmetros do indexador são colocados entre colchetes, assim como os índices de matriz, mas os parâmetros do indexador podem ser declarados para serem de qualquer tipo, ao contrário dos índices de matriz, que devem ser integrais.</span><span class="sxs-lookup"><span data-stu-id="768a7-112">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="768a7-113">Por exemplo, o .NET Framework define um tipo `Hashtable` que associa chaves e valores de tipo arbitrário:</span><span class="sxs-lookup"><span data-stu-id="768a7-113">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 <span data-ttu-id="768a7-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="768a7-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="768a7-115">Os colchetes também são usados para especificar [Atributos](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="768a7-115">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 <span data-ttu-id="768a7-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="768a7-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="768a7-117">Você pode usar colchetes para desindexar um ponteiro:</span><span class="sxs-lookup"><span data-stu-id="768a7-117">You can use square brackets to index off a pointer:</span></span>  
  
 <span data-ttu-id="768a7-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="768a7-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="768a7-119">Nenhuma verificação de limites é executada.</span><span class="sxs-lookup"><span data-stu-id="768a7-119">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="768a7-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="768a7-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="768a7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="768a7-121">See Also</span></span>  
 <span data-ttu-id="768a7-122">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="768a7-123">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="768a7-124">[Operadores do C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-124">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="768a7-125">[Matrizes](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-125">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="768a7-126">[Indexadores](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-126">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="768a7-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="768a7-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="768a7-128">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="768a7-128">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)

