---
title: "Conversões de ponteiro (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
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
ms.openlocfilehash: e415d892d979e2bdcd648256150e2a96b1772ce4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="f1535-102">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f1535-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="f1535-103">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="f1535-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="f1535-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="f1535-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="f1535-105">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="f1535-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="f1535-106">De</span><span class="sxs-lookup"><span data-stu-id="f1535-106">From</span></span>|<span data-ttu-id="f1535-107">Para</span><span class="sxs-lookup"><span data-stu-id="f1535-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f1535-108">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-108">Any pointer type</span></span>|<span data-ttu-id="f1535-109">void*</span><span class="sxs-lookup"><span data-stu-id="f1535-109">void*</span></span>|  
|<span data-ttu-id="f1535-110">nulo</span><span class="sxs-lookup"><span data-stu-id="f1535-110">null</span></span>|<span data-ttu-id="f1535-111">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="f1535-112">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="f1535-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="f1535-113">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="f1535-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="f1535-114">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="f1535-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="f1535-115">De</span><span class="sxs-lookup"><span data-stu-id="f1535-115">From</span></span>|<span data-ttu-id="f1535-116">Para</span><span class="sxs-lookup"><span data-stu-id="f1535-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="f1535-117">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-117">Any pointer type</span></span>|<span data-ttu-id="f1535-118">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-118">Any other pointer type</span></span>|  
|<span data-ttu-id="f1535-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="f1535-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="f1535-120">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-120">Any pointer type</span></span>|  
|<span data-ttu-id="f1535-121">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f1535-121">Any pointer type</span></span>|<span data-ttu-id="f1535-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="f1535-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f1535-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1535-123">Example</span></span>  
 <span data-ttu-id="f1535-124">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="f1535-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="f1535-125">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="f1535-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="f1535-126">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="f1535-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 <span data-ttu-id="f1535-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1535-127">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]</span></span>  
  
 <span data-ttu-id="f1535-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1535-128">[!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1535-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1535-129">See Also</span></span>  
 <span data-ttu-id="f1535-130">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f1535-131">[Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-131">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="f1535-132">[Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-132">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="f1535-133">[Tipos](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-133">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="f1535-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-134">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="f1535-135">[Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f1535-135">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="f1535-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f1535-136">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

