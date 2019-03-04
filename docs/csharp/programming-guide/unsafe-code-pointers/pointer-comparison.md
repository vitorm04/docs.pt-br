---
title: Comparação de ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969200"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="0159e-102">Comparação de ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0159e-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="0159e-103">É possível aplicar os seguintes operadores para comparar ponteiros de qualquer tipo:</span><span class="sxs-lookup"><span data-stu-id="0159e-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="0159e-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="0159e-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="0159e-105">Os operadores de comparação comparam os endereços dos dois operandos como se fossem inteiros sem sinal.</span><span class="sxs-lookup"><span data-stu-id="0159e-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0159e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0159e-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="0159e-107">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="0159e-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="0159e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0159e-108">See also</span></span>

- [<span data-ttu-id="0159e-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0159e-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0159e-110">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="0159e-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="0159e-111">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="0159e-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="0159e-112">Manipulando ponteiros</span><span class="sxs-lookup"><span data-stu-id="0159e-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="0159e-113">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="0159e-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0159e-114">Tipos</span><span class="sxs-lookup"><span data-stu-id="0159e-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="0159e-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="0159e-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="0159e-116">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="0159e-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="0159e-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0159e-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
