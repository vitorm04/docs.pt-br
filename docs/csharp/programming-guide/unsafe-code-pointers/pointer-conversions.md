---
title: Conversões de ponteiro – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745370"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="278ae-102">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="278ae-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="278ae-103">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="278ae-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="278ae-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="278ae-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="278ae-105">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="278ae-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="278ae-106">De</span><span class="sxs-lookup"><span data-stu-id="278ae-106">From</span></span>|<span data-ttu-id="278ae-107">Para</span><span class="sxs-lookup"><span data-stu-id="278ae-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="278ae-108">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-108">Any pointer type</span></span>|<span data-ttu-id="278ae-109">void\*</span><span class="sxs-lookup"><span data-stu-id="278ae-109">void\*</span></span>|  
|<span data-ttu-id="278ae-110">nulo</span><span class="sxs-lookup"><span data-stu-id="278ae-110">null</span></span>|<span data-ttu-id="278ae-111">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="278ae-112">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="278ae-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="278ae-113">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="278ae-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="278ae-114">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="278ae-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="278ae-115">De</span><span class="sxs-lookup"><span data-stu-id="278ae-115">From</span></span>|<span data-ttu-id="278ae-116">Para</span><span class="sxs-lookup"><span data-stu-id="278ae-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="278ae-117">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-117">Any pointer type</span></span>|<span data-ttu-id="278ae-118">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-118">Any other pointer type</span></span>|  
|<span data-ttu-id="278ae-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="278ae-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="278ae-120">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-120">Any pointer type</span></span>|  
|<span data-ttu-id="278ae-121">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-121">Any pointer type</span></span>|<span data-ttu-id="278ae-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="278ae-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="278ae-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="278ae-123">Example</span></span>  
 <span data-ttu-id="278ae-124">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="278ae-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="278ae-125">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="278ae-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="278ae-126">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="278ae-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="278ae-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="278ae-127">See also</span></span>

- [<span data-ttu-id="278ae-128">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="278ae-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="278ae-129">Tipos de Ponteiro</span><span class="sxs-lookup"><span data-stu-id="278ae-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="278ae-130">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="278ae-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="278ae-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="278ae-131">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="278ae-132">Inseguro</span><span class="sxs-lookup"><span data-stu-id="278ae-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="278ae-133">Declaração fixa</span><span class="sxs-lookup"><span data-stu-id="278ae-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="278ae-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="278ae-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
