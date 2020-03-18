---
title: Comparação entre propriedades e indexadores – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712124"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="56c17-102">Comparação entre propriedades e indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="56c17-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="56c17-103">Os indexadores são como propriedades.</span><span class="sxs-lookup"><span data-stu-id="56c17-103">Indexers are like properties.</span></span> <span data-ttu-id="56c17-104">Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.</span><span class="sxs-lookup"><span data-stu-id="56c17-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="56c17-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="56c17-105">Property</span></span>|<span data-ttu-id="56c17-106">Indexador</span><span class="sxs-lookup"><span data-stu-id="56c17-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="56c17-107">Permite que os métodos sejam chamados como se fossem membros de dados públicos.</span><span class="sxs-lookup"><span data-stu-id="56c17-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="56c17-108">Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="56c17-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="56c17-109">Acessado por meio de um nome simples.</span><span class="sxs-lookup"><span data-stu-id="56c17-109">Accessed through a simple name.</span></span>|<span data-ttu-id="56c17-110">Acessado por meio de um índice.</span><span class="sxs-lookup"><span data-stu-id="56c17-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="56c17-111">Pode ser estático ou um membro de instância.</span><span class="sxs-lookup"><span data-stu-id="56c17-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="56c17-112">Deve ser um membro da instância.</span><span class="sxs-lookup"><span data-stu-id="56c17-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="56c17-113">Um acessador [get](../../language-reference/keywords/get.md) de uma propriedade não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="56c17-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="56c17-114">Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.</span><span class="sxs-lookup"><span data-stu-id="56c17-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="56c17-115">Um acessador [set](../../language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.</span><span class="sxs-lookup"><span data-stu-id="56c17-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="56c17-116">Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../language-reference/keywords/value.md).</span><span class="sxs-lookup"><span data-stu-id="56c17-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="56c17-117">Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="56c17-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="56c17-118">Dá suporte a membros aptos para expressão a fim de obter somente indexadores.</span><span class="sxs-lookup"><span data-stu-id="56c17-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56c17-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="56c17-119">See also</span></span>

- [<span data-ttu-id="56c17-120">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="56c17-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="56c17-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="56c17-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="56c17-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="56c17-122">Properties</span></span>](../classes-and-structs/properties.md)
