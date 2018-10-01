---
title: Agrupar resultados por chaves contíguas (LINQ em C#)
description: Como agrupar resultados por chaves contíguas usando LINQ em C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47192999"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="70107-103">Agrupar resultados por chaves contíguas</span><span class="sxs-lookup"><span data-stu-id="70107-103">Group results by contiguous keys</span></span>

<span data-ttu-id="70107-104">O exemplo a seguir mostra como agrupar elementos em partes que representam subsequências de chaves contíguas.</span><span class="sxs-lookup"><span data-stu-id="70107-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="70107-105">Por exemplo, suponha que você receba a seguinte sequência de pares chave-valor:</span><span class="sxs-lookup"><span data-stu-id="70107-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="70107-106">Chave</span><span class="sxs-lookup"><span data-stu-id="70107-106">Key</span></span>|<span data-ttu-id="70107-107">Valor</span><span class="sxs-lookup"><span data-stu-id="70107-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="70107-108">Um</span><span class="sxs-lookup"><span data-stu-id="70107-108">A</span></span>|<span data-ttu-id="70107-109">We</span><span class="sxs-lookup"><span data-stu-id="70107-109">We</span></span>|
|<span data-ttu-id="70107-110">Um</span><span class="sxs-lookup"><span data-stu-id="70107-110">A</span></span>|<span data-ttu-id="70107-111">think</span><span class="sxs-lookup"><span data-stu-id="70107-111">think</span></span>|
|<span data-ttu-id="70107-112">Um</span><span class="sxs-lookup"><span data-stu-id="70107-112">A</span></span>|<span data-ttu-id="70107-113">that</span><span class="sxs-lookup"><span data-stu-id="70107-113">that</span></span>|
|<span data-ttu-id="70107-114">B</span><span class="sxs-lookup"><span data-stu-id="70107-114">B</span></span>|<span data-ttu-id="70107-115">Linq</span><span class="sxs-lookup"><span data-stu-id="70107-115">Linq</span></span>|
|<span data-ttu-id="70107-116">C</span><span class="sxs-lookup"><span data-stu-id="70107-116">C</span></span>|<span data-ttu-id="70107-117">is</span><span class="sxs-lookup"><span data-stu-id="70107-117">is</span></span>|
|<span data-ttu-id="70107-118">Um</span><span class="sxs-lookup"><span data-stu-id="70107-118">A</span></span>|<span data-ttu-id="70107-119">really</span><span class="sxs-lookup"><span data-stu-id="70107-119">really</span></span>|
|<span data-ttu-id="70107-120">B</span><span class="sxs-lookup"><span data-stu-id="70107-120">B</span></span>|<span data-ttu-id="70107-121">cool</span><span class="sxs-lookup"><span data-stu-id="70107-121">cool</span></span>|
|<span data-ttu-id="70107-122">B</span><span class="sxs-lookup"><span data-stu-id="70107-122">B</span></span>|<span data-ttu-id="70107-123">!</span><span class="sxs-lookup"><span data-stu-id="70107-123">!</span></span>|

<span data-ttu-id="70107-124">Os seguintes grupos serão criados nesta ordem:</span><span class="sxs-lookup"><span data-stu-id="70107-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="70107-125">We, think, that</span><span class="sxs-lookup"><span data-stu-id="70107-125">We, think, that</span></span>

2. <span data-ttu-id="70107-126">Linq</span><span class="sxs-lookup"><span data-stu-id="70107-126">Linq</span></span>

3. <span data-ttu-id="70107-127">is</span><span class="sxs-lookup"><span data-stu-id="70107-127">is</span></span>

4. <span data-ttu-id="70107-128">really</span><span class="sxs-lookup"><span data-stu-id="70107-128">really</span></span>

5. <span data-ttu-id="70107-129">cool, !</span><span class="sxs-lookup"><span data-stu-id="70107-129">cool, !</span></span>

<span data-ttu-id="70107-130">A solução é implementada como um método de extensão que é thread-safe e que retorna os resultados de uma maneira de streaming.</span><span class="sxs-lookup"><span data-stu-id="70107-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="70107-131">Em outras palavras, ela produz seus grupos à medida que percorre a sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="70107-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="70107-132">Diferentemente dos operadores `group` ou `orderby`, ela pode começar a retornar grupos para o chamador antes que todas as sequências sejam lidas.</span><span class="sxs-lookup"><span data-stu-id="70107-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="70107-133">O acesso thread-safe é alcançado ao fazer uma cópia de cada grupo ou parte enquanto a sequência de origem é iterada, conforme explicado nos comentários do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="70107-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="70107-134">Se a sequência de origem tiver uma sequência grande de itens contíguos, o Common Language Runtime poderá lançar uma <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="70107-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="70107-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70107-135">Example</span></span>

<span data-ttu-id="70107-136">O exemplo a seguir mostra o método de extensão e o código do cliente que o usa:</span><span class="sxs-lookup"><span data-stu-id="70107-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="70107-137">Para usar o método de extensão em seu projeto, copie a classe estática `MyExtensions` para um arquivo de código-fonte novo ou existente e se for necessário, adicione uma diretiva `using` para o namespace em que ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="70107-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="70107-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70107-138">See also</span></span>

- [<span data-ttu-id="70107-139">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="70107-139">Language Integrated Query (LINQ)</span></span>](index.md)
