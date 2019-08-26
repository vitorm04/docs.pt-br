---
title: Comparação entre propriedades e indexadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589472"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="35208-102">Comparação entre propriedades e indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="35208-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="35208-103">Os indexadores são como propriedades.</span><span class="sxs-lookup"><span data-stu-id="35208-103">Indexers are like properties.</span></span> <span data-ttu-id="35208-104">Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.</span><span class="sxs-lookup"><span data-stu-id="35208-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="35208-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="35208-105">Property</span></span>|<span data-ttu-id="35208-106">Indexador</span><span class="sxs-lookup"><span data-stu-id="35208-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="35208-107">Permite que os métodos sejam chamados como se fossem membros de dados públicos.</span><span class="sxs-lookup"><span data-stu-id="35208-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="35208-108">Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="35208-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="35208-109">Acessado por meio de um nome simples.</span><span class="sxs-lookup"><span data-stu-id="35208-109">Accessed through a simple name.</span></span>|<span data-ttu-id="35208-110">Acessado por meio de um índice.</span><span class="sxs-lookup"><span data-stu-id="35208-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="35208-111">Pode ser estático ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="35208-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="35208-112">Deve ser um membro da instância.</span><span class="sxs-lookup"><span data-stu-id="35208-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="35208-113">Um acessador [get](../../language-reference/keywords/get.md) de uma propriedade não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="35208-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="35208-114">Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.</span><span class="sxs-lookup"><span data-stu-id="35208-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="35208-115">Um acessador [set](../../language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.</span><span class="sxs-lookup"><span data-stu-id="35208-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="35208-116">Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="35208-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="35208-117">Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="35208-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="35208-118">Dá suporte a membros aptos para expressão a fim de obter somente indexadores.</span><span class="sxs-lookup"><span data-stu-id="35208-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35208-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35208-119">See also</span></span>

- [<span data-ttu-id="35208-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="35208-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35208-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="35208-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="35208-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="35208-122">Properties</span></span>](../classes-and-structs/properties.md)
