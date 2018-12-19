---
title: Comparação de ponteiros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 72d9017064959c801bd2702ff585ee16b1592da6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236785"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="c03a3-102">Comparação de ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c03a3-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="c03a3-103">É possível aplicar os seguintes operadores para comparar ponteiros de qualquer tipo:</span><span class="sxs-lookup"><span data-stu-id="c03a3-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="c03a3-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="c03a3-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="c03a3-105">Os operadores de comparação comparam os endereços dos dois operandos como se fossem inteiros sem sinal.</span><span class="sxs-lookup"><span data-stu-id="c03a3-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c03a3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c03a3-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="c03a3-107">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c03a3-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="c03a3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c03a3-108">See Also</span></span>

- [<span data-ttu-id="c03a3-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c03a3-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c03a3-110">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="c03a3-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="c03a3-111">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="c03a3-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="c03a3-112">Manipulando ponteiros</span><span class="sxs-lookup"><span data-stu-id="c03a3-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="c03a3-113">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="c03a3-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="c03a3-114">Tipos</span><span class="sxs-lookup"><span data-stu-id="c03a3-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="c03a3-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="c03a3-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="c03a3-116">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="c03a3-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="c03a3-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="c03a3-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
