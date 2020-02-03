---
title: Conversões de ponteiro – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745370"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="eb013-102">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="eb013-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="eb013-103">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="eb013-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="eb013-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="eb013-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="eb013-105">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="eb013-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="eb013-106">De</span><span class="sxs-lookup"><span data-stu-id="eb013-106">From</span></span>|<span data-ttu-id="eb013-107">{1&gt;Para&lt;1}</span><span class="sxs-lookup"><span data-stu-id="eb013-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="eb013-108">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-108">Any pointer type</span></span>|<span data-ttu-id="eb013-109">void\*</span><span class="sxs-lookup"><span data-stu-id="eb013-109">void\*</span></span>|  
|<span data-ttu-id="eb013-110">{1&gt;nulo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="eb013-110">null</span></span>|<span data-ttu-id="eb013-111">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="eb013-112">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="eb013-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="eb013-113">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="eb013-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="eb013-114">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="eb013-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="eb013-115">De</span><span class="sxs-lookup"><span data-stu-id="eb013-115">From</span></span>|<span data-ttu-id="eb013-116">{1&gt;Para&lt;1}</span><span class="sxs-lookup"><span data-stu-id="eb013-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="eb013-117">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-117">Any pointer type</span></span>|<span data-ttu-id="eb013-118">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-118">Any other pointer type</span></span>|  
|<span data-ttu-id="eb013-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="eb013-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="eb013-120">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-120">Any pointer type</span></span>|  
|<span data-ttu-id="eb013-121">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-121">Any pointer type</span></span>|<span data-ttu-id="eb013-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="eb013-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb013-123">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="eb013-123">Example</span></span>  
 <span data-ttu-id="eb013-124">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="eb013-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="eb013-125">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="eb013-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="eb013-126">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="eb013-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="eb013-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb013-127">See also</span></span>

- [<span data-ttu-id="eb013-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="eb013-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eb013-129">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="eb013-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="eb013-130">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="eb013-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="eb013-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="eb013-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="eb013-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="eb013-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="eb013-133">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="eb013-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="eb013-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="eb013-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
