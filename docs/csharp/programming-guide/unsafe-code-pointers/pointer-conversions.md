---
title: Conversões de ponteiro (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36589d139c91e04d9e3d8b31281a91c26b85a5d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="b2f2e-102">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b2f2e-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="b2f2e-103">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="b2f2e-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="b2f2e-105">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="b2f2e-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="b2f2e-106">De</span><span class="sxs-lookup"><span data-stu-id="b2f2e-106">From</span></span>|<span data-ttu-id="b2f2e-107">Para</span><span class="sxs-lookup"><span data-stu-id="b2f2e-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b2f2e-108">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-108">Any pointer type</span></span>|<span data-ttu-id="b2f2e-109">void\*</span><span class="sxs-lookup"><span data-stu-id="b2f2e-109">void\*</span></span>|  
|<span data-ttu-id="b2f2e-110">nulo</span><span class="sxs-lookup"><span data-stu-id="b2f2e-110">null</span></span>|<span data-ttu-id="b2f2e-111">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="b2f2e-112">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="b2f2e-113">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="b2f2e-114">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="b2f2e-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="b2f2e-115">De</span><span class="sxs-lookup"><span data-stu-id="b2f2e-115">From</span></span>|<span data-ttu-id="b2f2e-116">Para</span><span class="sxs-lookup"><span data-stu-id="b2f2e-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="b2f2e-117">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-117">Any pointer type</span></span>|<span data-ttu-id="b2f2e-118">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-118">Any other pointer type</span></span>|  
|<span data-ttu-id="b2f2e-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="b2f2e-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="b2f2e-120">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-120">Any pointer type</span></span>|  
|<span data-ttu-id="b2f2e-121">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-121">Any pointer type</span></span>|<span data-ttu-id="b2f2e-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="b2f2e-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2f2e-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2f2e-123">Example</span></span>  
 <span data-ttu-id="b2f2e-124">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="b2f2e-125">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="b2f2e-126">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="b2f2e-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b2f2e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2f2e-127">See Also</span></span>  
 [<span data-ttu-id="b2f2e-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b2f2e-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2f2e-129">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="b2f2e-130">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="b2f2e-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="b2f2e-131">Tipos</span><span class="sxs-lookup"><span data-stu-id="b2f2e-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="b2f2e-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="b2f2e-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="b2f2e-133">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="b2f2e-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="b2f2e-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b2f2e-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
