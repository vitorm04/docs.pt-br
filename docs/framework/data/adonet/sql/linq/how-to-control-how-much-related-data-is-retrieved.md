---
title: 'Como: controlar quantos dados relacionados são recuperados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215437"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="9fbcb-102">Como: controlar quantos dados relacionados são recuperados</span><span class="sxs-lookup"><span data-stu-id="9fbcb-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="9fbcb-103">Use o método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para especificar que os dados relacionados ao destino de chave devem ser recuperados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="9fbcb-104">Por exemplo, se você souber você precisará informações sobre os pedidos de clientes, você pode usar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para certificar-se de que as informações do pedido é recuperada ao mesmo tempo que informações para o cliente.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="9fbcb-105">Essa abordagem resulta em apenas um processamento para o base de dados para ambos os conjuntos de informações.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fbcb-106">Você pode recuperar os dados relacionados ao destino principal da sua consulta recuperando entre um produto como uma grande projeção, como recuperar pedidos quando você seleciona clientes.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="9fbcb-107">Mas essa abordagem tem geralmente desvantagens.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="9fbcb-108">Por exemplo, os resultados são apenas as projeções e não as entidades que podem ser alteradas e mantidas por [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fbcb-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9fbcb-109">E você pode recuperar grandes quantidades de dados que você não precisa.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fbcb-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fbcb-110">Example</span></span>  
 <span data-ttu-id="9fbcb-111">No exemplo a seguir, qualquer `Orders` para qualquer `Customers` que está localizado em Londres é recuperado quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="9fbcb-112">Como resultado, o acesso são a propriedade de `Orders` em um objeto de `Customer` não dispara uma nova consulta de base de dados.</span><span class="sxs-lookup"><span data-stu-id="9fbcb-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9fbcb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fbcb-113">See also</span></span>

- [<span data-ttu-id="9fbcb-114">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="9fbcb-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
