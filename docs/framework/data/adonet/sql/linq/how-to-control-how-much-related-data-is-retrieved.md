---
title: 'Como: controlar quantos dados relacionados são recuperados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782060"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="e469e-102">Como: controlar quantos dados relacionados são recuperados</span><span class="sxs-lookup"><span data-stu-id="e469e-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="e469e-103">Use o método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para especificar que os dados relacionados ao destino de chave devem ser recuperados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="e469e-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="e469e-104">Por exemplo, se você souber você precisará informações sobre os pedidos de clientes, você pode usar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para certificar-se de que as informações do pedido é recuperada ao mesmo tempo que informações para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e469e-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="e469e-105">Essa abordagem resulta em apenas um processamento para o base de dados para ambos os conjuntos de informações.</span><span class="sxs-lookup"><span data-stu-id="e469e-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e469e-106">Você pode recuperar os dados relacionados ao destino principal da sua consulta recuperando entre um produto como uma grande projeção, como recuperar pedidos quando você seleciona clientes.</span><span class="sxs-lookup"><span data-stu-id="e469e-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="e469e-107">Mas essa abordagem tem geralmente desvantagens.</span><span class="sxs-lookup"><span data-stu-id="e469e-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="e469e-108">Por exemplo, os resultados são apenas projeções e não entidades que podem ser alteradas e persistidas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pelo.</span><span class="sxs-lookup"><span data-stu-id="e469e-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e469e-109">E você pode recuperar muitos dados que não são necessários.</span><span class="sxs-lookup"><span data-stu-id="e469e-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e469e-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e469e-110">Example</span></span>  
 <span data-ttu-id="e469e-111">No exemplo a seguir, qualquer `Orders` para qualquer `Customers` que está localizado em Londres é recuperado quando a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="e469e-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="e469e-112">Como resultado, o acesso são a propriedade de `Orders` em um objeto de `Customer` não dispara uma nova consulta de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e469e-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e469e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e469e-113">See also</span></span>

- [<span data-ttu-id="e469e-114">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="e469e-114">Querying the Database</span></span>](querying-the-database.md)
