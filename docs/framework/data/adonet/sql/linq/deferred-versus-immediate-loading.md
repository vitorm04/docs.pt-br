---
title: Adiado contra a carga immediate
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 992d9a018f81bbd3f0c9204168f513024769e079
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="108a6-102">Adiado contra a carga immediate</span><span class="sxs-lookup"><span data-stu-id="108a6-102">Deferred versus Immediate Loading</span></span>
<span data-ttu-id="108a6-103">Quando você consulta para um objeto, você só retorna o objeto que você solicitou.</span><span class="sxs-lookup"><span data-stu-id="108a6-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="108a6-104">O *relacionados* objetos não são buscados automaticamente ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="108a6-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="108a6-105">(Para obter mais informações, consulte [consulta entre relações](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Você não pode ver o fato de que os objetos relacionados não são carregados já, porque uma tentativa de acessar gerencia uma solicitação que recupere-os.</span><span class="sxs-lookup"><span data-stu-id="108a6-105">(For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="108a6-106">Por exemplo, você pode desejar consultar um determinado conjunto de pedidos e depois envie apenas ocasionalmente um email de notificação para clientes específicos.</span><span class="sxs-lookup"><span data-stu-id="108a6-106">For example, you might want to query for a particular set of orders and then only occasionally send an e-mail notification to particular customers.</span></span> <span data-ttu-id="108a6-107">Você não precisará necessariamente inicialmente de recuperar todos os dados do cliente com cada pedido.</span><span class="sxs-lookup"><span data-stu-id="108a6-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="108a6-108">Você pode usar o carregamento adiada para adiar a recuperação de informações extras até que você tenha que absolutamente.</span><span class="sxs-lookup"><span data-stu-id="108a6-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="108a6-109">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="108a6-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="108a6-110">O oposto também pode ser true.</span><span class="sxs-lookup"><span data-stu-id="108a6-110">The opposite might also be true.</span></span> <span data-ttu-id="108a6-111">Você pode ter um aplicativo que tenha que exibir o cliente e ordenação dados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="108a6-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="108a6-112">Você conhece-o necessidade dois conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="108a6-112">You know you need both sets of data.</span></span> <span data-ttu-id="108a6-113">Você sabe suas informações de ordem das necessidades do aplicativo para cada cliente para que você obter os resultados.</span><span class="sxs-lookup"><span data-stu-id="108a6-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="108a6-114">Você não deve enviar para consultas individuais de pedidos para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="108a6-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="108a6-115">O que você deseja realmente é recuperar os dados de pedidos juntamente com os clientes.</span><span class="sxs-lookup"><span data-stu-id="108a6-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="108a6-116">Você também pode associar à clientes e pedidos em uma consulta formando entre o produto e recuperar todos os bits de dados relacionados como uma grande projeção.</span><span class="sxs-lookup"><span data-stu-id="108a6-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="108a6-117">Mas esses resultados não são entidades.</span><span class="sxs-lookup"><span data-stu-id="108a6-117">But these results are not entities.</span></span> <span data-ttu-id="108a6-118">(Para obter mais informações, consulte [o LINQ no modelo de objeto SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span><span class="sxs-lookup"><span data-stu-id="108a6-118">(For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="108a6-119">As entidades são objetos que possuem a identidade e que você pode alterar, enquanto esses resultados seriam as projeções que não podem ser modificadas e persistente.</span><span class="sxs-lookup"><span data-stu-id="108a6-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="108a6-120">Ainda pior, você poderia ser recuperando lotes de dados redundantes como as repetições de cada cliente para cada ordem em aplainado se associam a saída.</span><span class="sxs-lookup"><span data-stu-id="108a6-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="108a6-121">O que você precisa realmente é uma maneira para recuperar ao mesmo tempo um conjunto de objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="108a6-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="108a6-122">O conjunto é uma seção delineado de um gráfico de modo que você nunca está recuperando mais ou menos que foi necessário para seu uso pretendido.</span><span class="sxs-lookup"><span data-stu-id="108a6-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="108a6-123">Para essa finalidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece <xref:System.Data.Linq.DataLoadOptions> para carregamento imediato de uma região do seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="108a6-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="108a6-124">Os métodos incluem:</span><span class="sxs-lookup"><span data-stu-id="108a6-124">Methods include:</span></span>  
  
-   <span data-ttu-id="108a6-125">O método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> , imediatamente para carregar os dados relacionados ao destino principal.</span><span class="sxs-lookup"><span data-stu-id="108a6-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
-   <span data-ttu-id="108a6-126">O método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> , para filtrar os objetos recuperados para um relacionamento específico.</span><span class="sxs-lookup"><span data-stu-id="108a6-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108a6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="108a6-127">See Also</span></span>  
 [<span data-ttu-id="108a6-128">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="108a6-128">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
