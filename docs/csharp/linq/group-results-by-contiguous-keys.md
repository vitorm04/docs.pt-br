---
title: "Agrupar resultados por chaves contíguas"
description: "Como agrupar resultados por chaves contíguas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ddd028a3aad5186ef6773b32e9f9e8e1cbff95fc
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="99bfe-104">Agrupar resultados por chaves contíguas</span><span class="sxs-lookup"><span data-stu-id="99bfe-104">Group results by contiguous keys</span></span>

<span data-ttu-id="99bfe-105">O exemplo a seguir mostra como agrupar elementos em partes que representam subsequências de chaves contíguas.</span><span class="sxs-lookup"><span data-stu-id="99bfe-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="99bfe-106">Por exemplo, suponha que você receba a seguinte sequência de pares chave-valor:</span><span class="sxs-lookup"><span data-stu-id="99bfe-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="99bfe-107">Chave</span><span class="sxs-lookup"><span data-stu-id="99bfe-107">Key</span></span>|<span data-ttu-id="99bfe-108">Valor</span><span class="sxs-lookup"><span data-stu-id="99bfe-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="99bfe-109">Um</span><span class="sxs-lookup"><span data-stu-id="99bfe-109">A</span></span>|<span data-ttu-id="99bfe-110">We</span><span class="sxs-lookup"><span data-stu-id="99bfe-110">We</span></span>|  
|<span data-ttu-id="99bfe-111">Um</span><span class="sxs-lookup"><span data-stu-id="99bfe-111">A</span></span>|<span data-ttu-id="99bfe-112">think</span><span class="sxs-lookup"><span data-stu-id="99bfe-112">think</span></span>|  
|<span data-ttu-id="99bfe-113">Um</span><span class="sxs-lookup"><span data-stu-id="99bfe-113">A</span></span>|<span data-ttu-id="99bfe-114">that</span><span class="sxs-lookup"><span data-stu-id="99bfe-114">that</span></span>|  
|<span data-ttu-id="99bfe-115">B</span><span class="sxs-lookup"><span data-stu-id="99bfe-115">B</span></span>|<span data-ttu-id="99bfe-116">Linq</span><span class="sxs-lookup"><span data-stu-id="99bfe-116">Linq</span></span>|  
|<span data-ttu-id="99bfe-117">C</span><span class="sxs-lookup"><span data-stu-id="99bfe-117">C</span></span>|<span data-ttu-id="99bfe-118">is</span><span class="sxs-lookup"><span data-stu-id="99bfe-118">is</span></span>|  
|<span data-ttu-id="99bfe-119">Um</span><span class="sxs-lookup"><span data-stu-id="99bfe-119">A</span></span>|<span data-ttu-id="99bfe-120">really</span><span class="sxs-lookup"><span data-stu-id="99bfe-120">really</span></span>|  
|<span data-ttu-id="99bfe-121">B</span><span class="sxs-lookup"><span data-stu-id="99bfe-121">B</span></span>|<span data-ttu-id="99bfe-122">cool</span><span class="sxs-lookup"><span data-stu-id="99bfe-122">cool</span></span>|  
|<span data-ttu-id="99bfe-123">B</span><span class="sxs-lookup"><span data-stu-id="99bfe-123">B</span></span>|<span data-ttu-id="99bfe-124">!</span><span class="sxs-lookup"><span data-stu-id="99bfe-124">!</span></span>|  
  
 <span data-ttu-id="99bfe-125">Os seguintes grupos serão criados nesta ordem:</span><span class="sxs-lookup"><span data-stu-id="99bfe-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="99bfe-126">We, think, that</span><span class="sxs-lookup"><span data-stu-id="99bfe-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="99bfe-127">Linq</span><span class="sxs-lookup"><span data-stu-id="99bfe-127">Linq</span></span>  
  
3.  <span data-ttu-id="99bfe-128">is</span><span class="sxs-lookup"><span data-stu-id="99bfe-128">is</span></span>  
  
4.  <span data-ttu-id="99bfe-129">really</span><span class="sxs-lookup"><span data-stu-id="99bfe-129">really</span></span>  
  
5.  <span data-ttu-id="99bfe-130">cool, !</span><span class="sxs-lookup"><span data-stu-id="99bfe-130">cool, !</span></span>  
  
 <span data-ttu-id="99bfe-131">A solução é implementada como um método de extensão que é thread-safe e que retorna os resultados de uma maneira de streaming.</span><span class="sxs-lookup"><span data-stu-id="99bfe-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="99bfe-132">Em outras palavras, ela produz seus grupos à medida que percorre a sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="99bfe-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="99bfe-133">Diferentemente dos operadores `group` ou `orderby`, ela pode começar a retornar grupos para o chamador antes que todas as sequências sejam lidas.</span><span class="sxs-lookup"><span data-stu-id="99bfe-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="99bfe-134">O acesso thread-safe é alcançado ao fazer uma cópia de cada grupo ou parte enquanto a sequência de origem é iterada, conforme explicado nos comentários do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="99bfe-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="99bfe-135">Se a sequência de origem tiver uma sequência grande de itens contíguos, o Common Language Runtime poderá lançar uma <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="99bfe-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99bfe-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99bfe-136">Example</span></span>  
 <span data-ttu-id="99bfe-137">O exemplo a seguir mostra o método de extensão e o código cliente que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="99bfe-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 <span data-ttu-id="99bfe-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="99bfe-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span></span>  
  
 <span data-ttu-id="99bfe-139">Para usar o método de extensão em seu projeto, copie a classe estática `MyExtensions` para um arquivo de código-fonte novo ou existente e se for necessário, adicione uma diretiva `using` para o namespace em que ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="99bfe-139">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bfe-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99bfe-140">See also</span></span>  
 [<span data-ttu-id="99bfe-141">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="99bfe-141">LINQ Query Expressions</span></span>](index.md)   
 

