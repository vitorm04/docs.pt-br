---
title: Conversões de ponteiro – Guia de Programação em C#
description: Saiba mais sobre conversões de ponteiro. Consulte tabelas de conversões de ponteiro implícitas e explícitas, exemplos de código e exibir recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: c39be5cb52964abbea5bc5636c6fa74d8411a331
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382081"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="9789e-104">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9789e-104">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="9789e-105">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="9789e-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="9789e-106">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="9789e-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="9789e-107">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="9789e-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="9789e-108">De</span><span class="sxs-lookup"><span data-stu-id="9789e-108">From</span></span>|<span data-ttu-id="9789e-109">Para</span><span class="sxs-lookup"><span data-stu-id="9789e-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="9789e-110">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-110">Any pointer type</span></span>|<span data-ttu-id="9789e-111">void\*</span><span class="sxs-lookup"><span data-stu-id="9789e-111">void\*</span></span>|  
|<span data-ttu-id="9789e-112">nulo</span><span class="sxs-lookup"><span data-stu-id="9789e-112">null</span></span>|<span data-ttu-id="9789e-113">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="9789e-114">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="9789e-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="9789e-115">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="9789e-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="9789e-116">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="9789e-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="9789e-117">De</span><span class="sxs-lookup"><span data-stu-id="9789e-117">From</span></span>|<span data-ttu-id="9789e-118">Para</span><span class="sxs-lookup"><span data-stu-id="9789e-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="9789e-119">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-119">Any pointer type</span></span>|<span data-ttu-id="9789e-120">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-120">Any other pointer type</span></span>|  
|<span data-ttu-id="9789e-121">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="9789e-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="9789e-122">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-122">Any pointer type</span></span>|  
|<span data-ttu-id="9789e-123">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-123">Any pointer type</span></span>|<span data-ttu-id="9789e-124">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="9789e-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9789e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9789e-125">Example</span></span>  
 <span data-ttu-id="9789e-126">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="9789e-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="9789e-127">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="9789e-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="9789e-128">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="9789e-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9789e-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="9789e-129">See also</span></span>

- [<span data-ttu-id="9789e-130">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="9789e-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9789e-131">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="9789e-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="9789e-132">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="9789e-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="9789e-133">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="9789e-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="9789e-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="9789e-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="9789e-135">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="9789e-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="9789e-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="9789e-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
