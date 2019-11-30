---
title: Como definir uma operação de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569136"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="c977c-102">Como definir uma operação de serviço (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c977c-102">How to: Define a Service Operation (WCF Data Services)</span></span>

<span data-ttu-id="c977c-103">WCF Data Services expor métodos que são definidos no servidor como operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="c977c-103">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="c977c-104">As operações de serviço permitem que um serviço de dados forneça acesso por meio de um URI para um método definido no servidor.</span><span class="sxs-lookup"><span data-stu-id="c977c-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="c977c-105">Para definir uma operação de serviço, aplique o atributo [`WebGet]` ou `[WebInvoke]` ao método.</span><span class="sxs-lookup"><span data-stu-id="c977c-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="c977c-106">Para dar suporte a operadores de consulta, a operação de serviço deve retornar uma instância de <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="c977c-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="c977c-107">As operações de serviço podem acessar a fonte de dados subjacente por meio da propriedade <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> no <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="c977c-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="c977c-108">Para obter mais informações, consulte [operações de serviço](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c977c-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="c977c-109">O exemplo neste tópico define uma operação de serviço chamada `GetOrdersByCity` que retorna uma instância de <xref:System.Linq.IQueryable%601> filtrada de `Orders` e objetos `Order_Details` relacionados.</span><span class="sxs-lookup"><span data-stu-id="c977c-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="c977c-110">O exemplo acessa a instância de <xref:System.Data.Objects.ObjectContext> que é a fonte de dados para o serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="c977c-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="c977c-111">Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c977c-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="c977c-112">Para definir uma operação de serviço no serviço de dados Northwind</span><span class="sxs-lookup"><span data-stu-id="c977c-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="c977c-113">No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="c977c-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="c977c-114">Na classe `Northwind`, defina um método de operação de serviço chamado `GetOrdersByCity` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c977c-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="c977c-115">No método `InitializeService` da classe `Northwind`, adicione o seguinte código para habilitar o acesso à operação de serviço:</span><span class="sxs-lookup"><span data-stu-id="c977c-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="c977c-116">Para consultar a operação do serviço GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="c977c-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="c977c-117">Em um navegador da Web, insira um dos seguintes URIs para invocar a operação de serviço que é definida no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c977c-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="c977c-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c977c-118">Example</span></span>

<span data-ttu-id="c977c-119">O exemplo a seguir implementa uma operação de serviço chamada `GetOrderByCity` no serviço de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="c977c-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="c977c-120">Esta operação usa o Entity Framework ADO.NET para retornar um conjunto de `Orders` e objetos `Order_Details` relacionados como uma instância de <xref:System.Linq.IQueryable%601> com base no nome de cidade fornecido.</span><span class="sxs-lookup"><span data-stu-id="c977c-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="c977c-121">Há suporte para operadores de consulta neste ponto de extremidade de operação de serviço porque o método retorna uma instância de <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="c977c-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="c977c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c977c-122">See also</span></span>

- <span data-ttu-id="c977c-123">[Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c977c-123">[Defining WCF Data Services](defining-wcf-data-services.md)</span></span>
