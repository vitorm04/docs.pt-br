---
title: Conversões de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 663599ab9ba6755388603d5d3cc5a9ee522f3c9f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345649"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="3f102-102">Conversões de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3f102-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="3f102-103">A tabela a seguir mostra as conversões de ponteiro implícitas predefinidas.</span><span class="sxs-lookup"><span data-stu-id="3f102-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="3f102-104">As conversões implícitas podem ocorrer em diversas situações, incluindo instruções de atribuição e invocações de método.</span><span class="sxs-lookup"><span data-stu-id="3f102-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="3f102-105">Conversões de ponteiro implícitas</span><span class="sxs-lookup"><span data-stu-id="3f102-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="3f102-106">Do</span><span class="sxs-lookup"><span data-stu-id="3f102-106">From</span></span>|<span data-ttu-id="3f102-107">{1&gt;Para&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3f102-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3f102-108">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-108">Any pointer type</span></span>|<span data-ttu-id="3f102-109">void\*</span><span class="sxs-lookup"><span data-stu-id="3f102-109">void\*</span></span>|  
|<span data-ttu-id="3f102-110">{1&gt;nulo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3f102-110">null</span></span>|<span data-ttu-id="3f102-111">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="3f102-112">A conversão explícita de ponteiro é usada para realizar conversões para as quais não há conversão implícita, usando uma expressão de conversão.</span><span class="sxs-lookup"><span data-stu-id="3f102-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="3f102-113">A tabela a seguir mostra essas conversões.</span><span class="sxs-lookup"><span data-stu-id="3f102-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="3f102-114">Conversões de ponteiro explícitas</span><span class="sxs-lookup"><span data-stu-id="3f102-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="3f102-115">Do</span><span class="sxs-lookup"><span data-stu-id="3f102-115">From</span></span>|<span data-ttu-id="3f102-116">{1&gt;Para&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3f102-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="3f102-117">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-117">Any pointer type</span></span>|<span data-ttu-id="3f102-118">Qualquer outro tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-118">Any other pointer type</span></span>|  
|<span data-ttu-id="3f102-119">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="3f102-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="3f102-120">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-120">Any pointer type</span></span>|  
|<span data-ttu-id="3f102-121">Qualquer tipo de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-121">Any pointer type</span></span>|<span data-ttu-id="3f102-122">sbyte, byte, short, ushort, int, uint, long ou ulong</span><span class="sxs-lookup"><span data-stu-id="3f102-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f102-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f102-123">Example</span></span>  
 <span data-ttu-id="3f102-124">No exemplo a seguir, um ponteiro para `int` é convertido em um ponteiro para `byte`.</span><span class="sxs-lookup"><span data-stu-id="3f102-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="3f102-125">Observe que o ponteiro aponta para o menor byte endereçado da variável.</span><span class="sxs-lookup"><span data-stu-id="3f102-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="3f102-126">Quando você incrementar sucessivamente o resultado, até o tamanho de `int` (4 bytes), você poderá exibir os bytes restantes da variável.</span><span class="sxs-lookup"><span data-stu-id="3f102-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3f102-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="3f102-127">See also</span></span>

- [<span data-ttu-id="3f102-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3f102-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f102-129">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="3f102-129">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="3f102-130">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="3f102-130">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="3f102-131">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="3f102-131">Value types</span></span>](../../language-reference/keywords/value-types.md)
- [<span data-ttu-id="3f102-132">unsafe</span><span class="sxs-lookup"><span data-stu-id="3f102-132">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="3f102-133">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="3f102-133">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="3f102-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3f102-134">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
