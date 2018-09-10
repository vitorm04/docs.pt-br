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
ms.openlocfilehash: 19283a795f8cfc444dfcb186dcecc0ea86eb27fd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500446"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cc4cb-102">Operador [] (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cc4cb-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="cc4cb-103">Os colchetes (`[]`) são usados para matrizes, indexadores e atributos.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="cc4cb-104">Eles também podem ser usados com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc4cb-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc4cb-105">Remarks</span></span>  
 <span data-ttu-id="cc4cb-106">Um tipo de matriz é um tipo seguido por `[]`:</span><span class="sxs-lookup"><span data-stu-id="cc4cb-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="cc4cb-107">Para acessar um elemento de uma matriz, o índice do elemento desejado é colocado entre colchetes:</span><span class="sxs-lookup"><span data-stu-id="cc4cb-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="cc4cb-108">Uma exceção será lançada se um índice de matriz estiver fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="cc4cb-109">O operador de indexação da matriz não pode ser sobrecarregado. No entanto, os tipos podem definir indexadores que recebem um ou mais parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="cc4cb-110">Os parâmetros do indexador são colocados entre colchetes, assim como os índices de matriz, mas os parâmetros do indexador podem ser declarados para serem de qualquer tipo, ao contrário dos índices de matriz, que devem ser integrais.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="cc4cb-111">Por exemplo, o .NET Framework define um tipo `Hashtable` que associa chaves e valores de tipo arbitrário:</span><span class="sxs-lookup"><span data-stu-id="cc4cb-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="cc4cb-112">Os colchetes também são usados para especificar [Atributos](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="cc4cb-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="cc4cb-113">Você pode usar colchetes para desindexar um ponteiro:</span><span class="sxs-lookup"><span data-stu-id="cc4cb-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="cc4cb-114">Nenhuma verificação de limites é executada.</span><span class="sxs-lookup"><span data-stu-id="cc4cb-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cc4cb-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cc4cb-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc4cb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc4cb-116">See Also</span></span>

- [<span data-ttu-id="cc4cb-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="cc4cb-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cc4cb-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cc4cb-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cc4cb-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="cc4cb-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="cc4cb-120">Matrizes</span><span class="sxs-lookup"><span data-stu-id="cc4cb-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="cc4cb-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="cc4cb-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="cc4cb-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="cc4cb-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="cc4cb-123">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="cc4cb-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
