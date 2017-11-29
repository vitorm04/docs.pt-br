---
title: "Comparação entre propriedades e indexadores (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 102a6a97726fa19fcba0e6f19876a3935e8625f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="76ac1-102">Comparação entre propriedades e indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="76ac1-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="76ac1-103">Os indexadores são como propriedades.</span><span class="sxs-lookup"><span data-stu-id="76ac1-103">Indexers are like properties.</span></span> <span data-ttu-id="76ac1-104">Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.</span><span class="sxs-lookup"><span data-stu-id="76ac1-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="76ac1-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="76ac1-105">Property</span></span>|<span data-ttu-id="76ac1-106">Indexador</span><span class="sxs-lookup"><span data-stu-id="76ac1-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="76ac1-107">Permite que os métodos sejam chamados como se fossem membros de dados públicos.</span><span class="sxs-lookup"><span data-stu-id="76ac1-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="76ac1-108">Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="76ac1-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="76ac1-109">Acessado por meio de um nome simples.</span><span class="sxs-lookup"><span data-stu-id="76ac1-109">Accessed through a simple name.</span></span>|<span data-ttu-id="76ac1-110">Acessado por meio de um índice.</span><span class="sxs-lookup"><span data-stu-id="76ac1-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="76ac1-111">Pode ser estático ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="76ac1-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="76ac1-112">Deve ser um membro da instância.</span><span class="sxs-lookup"><span data-stu-id="76ac1-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="76ac1-113">Um acessador [get](../../../csharp/language-reference/keywords/get.md) de uma propriedade não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="76ac1-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="76ac1-114">Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.</span><span class="sxs-lookup"><span data-stu-id="76ac1-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="76ac1-115">Um acessador [set](../../../csharp/language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.</span><span class="sxs-lookup"><span data-stu-id="76ac1-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="76ac1-116">Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../../csharp/language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="76ac1-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="76ac1-117">Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="76ac1-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="76ac1-118">Não oferece suporte a sintaxe reduzida.</span><span class="sxs-lookup"><span data-stu-id="76ac1-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76ac1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76ac1-119">See Also</span></span>  
 [<span data-ttu-id="76ac1-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="76ac1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76ac1-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="76ac1-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="76ac1-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="76ac1-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
