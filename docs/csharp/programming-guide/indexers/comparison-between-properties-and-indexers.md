---
title: Comparação entre propriedades e indexadores – Guia de Programação em C#
description: Compare como os indexadores em C# são como propriedades. Exceto para algumas diferenças, as regras definidas para acessadores de propriedade se aplicam aos acessadores do indexador.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192523"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="2f485-104">Comparação entre propriedades e indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2f485-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="2f485-105">Os indexadores são como propriedades.</span><span class="sxs-lookup"><span data-stu-id="2f485-105">Indexers are like properties.</span></span> <span data-ttu-id="2f485-106">Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.</span><span class="sxs-lookup"><span data-stu-id="2f485-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="2f485-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2f485-107">Property</span></span>|<span data-ttu-id="2f485-108">Indexador</span><span class="sxs-lookup"><span data-stu-id="2f485-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2f485-109">Permite que os métodos sejam chamados como se fossem membros de dados públicos.</span><span class="sxs-lookup"><span data-stu-id="2f485-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="2f485-110">Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="2f485-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="2f485-111">Acessado por meio de um nome simples.</span><span class="sxs-lookup"><span data-stu-id="2f485-111">Accessed through a simple name.</span></span>|<span data-ttu-id="2f485-112">Acessado por meio de um índice.</span><span class="sxs-lookup"><span data-stu-id="2f485-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="2f485-113">Pode ser estático ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="2f485-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="2f485-114">Deve ser um membro da instância.</span><span class="sxs-lookup"><span data-stu-id="2f485-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="2f485-115">Um acessador [get](../../language-reference/keywords/get.md) de uma propriedade não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2f485-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="2f485-116">Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.</span><span class="sxs-lookup"><span data-stu-id="2f485-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="2f485-117">Um acessador [set](../../language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.</span><span class="sxs-lookup"><span data-stu-id="2f485-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="2f485-118">Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="2f485-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="2f485-119">Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2f485-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="2f485-120">Dá suporte a membros aptos para expressão a fim de obter somente indexadores.</span><span class="sxs-lookup"><span data-stu-id="2f485-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f485-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="2f485-121">See also</span></span>

- [<span data-ttu-id="2f485-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="2f485-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2f485-123">Indexadores</span><span class="sxs-lookup"><span data-stu-id="2f485-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="2f485-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2f485-124">Properties</span></span>](../classes-and-structs/properties.md)
