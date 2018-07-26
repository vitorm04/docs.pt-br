---
title: Operador [] (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961426"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="933bc-102">Operador [] (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="933bc-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="933bc-103">Os colchetes (`[]`) são usados para matrizes, indexadores e atributos.</span><span class="sxs-lookup"><span data-stu-id="933bc-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="933bc-104">Eles também podem ser usados com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="933bc-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="933bc-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="933bc-105">Remarks</span></span>  
 <span data-ttu-id="933bc-106">Um tipo de matriz é um tipo seguido por `[]`:</span><span class="sxs-lookup"><span data-stu-id="933bc-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="933bc-107">Para acessar um elemento de uma matriz, o índice do elemento desejado é colocado entre colchetes:</span><span class="sxs-lookup"><span data-stu-id="933bc-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="933bc-108">Uma exceção será lançada se um índice de matriz estiver fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="933bc-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="933bc-109">O operador de indexação da matriz não pode ser sobrecarregado. No entanto, os tipos podem definir indexadores e propriedades que recebem um ou mais parâmetros.</span><span class="sxs-lookup"><span data-stu-id="933bc-109">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="933bc-110">Os parâmetros do indexador são colocados entre colchetes, assim como os índices de matriz, mas os parâmetros do indexador podem ser declarados para serem de qualquer tipo, ao contrário dos índices de matriz, que devem ser integrais.</span><span class="sxs-lookup"><span data-stu-id="933bc-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="933bc-111">Por exemplo, o .NET Framework define um tipo `Hashtable` que associa chaves e valores de tipo arbitrário:</span><span class="sxs-lookup"><span data-stu-id="933bc-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="933bc-112">Os colchetes também são usados para especificar [Atributos](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="933bc-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="933bc-113">Você pode usar colchetes para desindexar um ponteiro:</span><span class="sxs-lookup"><span data-stu-id="933bc-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="933bc-114">Nenhuma verificação de limites é executada.</span><span class="sxs-lookup"><span data-stu-id="933bc-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="933bc-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="933bc-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="933bc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="933bc-116">See Also</span></span>  
 [<span data-ttu-id="933bc-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="933bc-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="933bc-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="933bc-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="933bc-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="933bc-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="933bc-120">Matrizes</span><span class="sxs-lookup"><span data-stu-id="933bc-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="933bc-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="933bc-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="933bc-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="933bc-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="933bc-123">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="933bc-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
