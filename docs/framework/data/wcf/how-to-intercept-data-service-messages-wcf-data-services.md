---
title: "Como interceptar mensagens de serviço de dados (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c18664eaa154fbc048c77cb359d0926f04b7e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="9bc6b-102">Como interceptar mensagens de serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9bc6b-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="9bc6b-103">Com o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você pode interceptar mensagens de solicitação de modo que você possa adicionar lógica personalizada a uma operação.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="9bc6b-104">Para interceptar uma mensagem, você pode usar métodos especialmente atribuídos no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="9bc6b-105">Para obter mais informações, consulte [interceptores](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9bc6b-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="9bc6b-106">O exemplo neste tópico usa o serviço de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="9bc6b-107">Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9bc6b-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="9bc6b-108">Para definir um interceptor de consulta para o conjunto de entidades Orders</span><span class="sxs-lookup"><span data-stu-id="9bc6b-108">To define a query interceptor for the Orders entity set</span></span>  
  
1.  <span data-ttu-id="9bc6b-109">No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="9bc6b-110">Na página de código para a classe `Northwind`, adicione a instrução `using` a seguir (`Imports` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9bc6b-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  <span data-ttu-id="9bc6b-111">Na classe `Northwind`, defina um método de operação de serviço chamado `OnQueryOrders` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9bc6b-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="9bc6b-112">Para definir um interceptor de alteração para o conjunto de entidades Products</span><span class="sxs-lookup"><span data-stu-id="9bc6b-112">To define a change interceptor for the Products entity set</span></span>  
  
1.  <span data-ttu-id="9bc6b-113">No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="9bc6b-114">Na classe `Northwind`, defina um método de operação de serviço chamado `OnChangeProducts` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9bc6b-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="9bc6b-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bc6b-115">Example</span></span>  
 <span data-ttu-id="9bc6b-116">Este exemplo define um método de interceptor de consulta para o conjunto de entidades `Orders` que retorna uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="9bc6b-117">Esta expressão contém um delegado que filtra `Orders` solicitado com base em `Customers` relacionado que tem um nome de contato específico.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="9bc6b-118">O nome, por sua vez, é determinado com base no usuário solicitante.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="9bc6b-119">Este exemplo presume que o serviço de dados esteja hospedado dentro de um aplicativo ASP.NET que usa WCF, e a autenticação esteja habilitada.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="9bc6b-120">A classe <xref:System.Web.HttpContext> é usada para recuperar o princípio da solicitação atual.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="9bc6b-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bc6b-121">Example</span></span>  
 <span data-ttu-id="9bc6b-122">Este exemplo define um método de interceptador de alteração para o conjunto de entidades `Products`.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="9bc6b-123">Este método valida a entrada para o serviço para uma operação <xref:System.Data.Services.UpdateOperations.Add> ou <xref:System.Data.Services.UpdateOperations.Change> e gera uma exceção se uma alteração está sendo feita a um produto descontinuado.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="9bc6b-124">Ele também bloqueia a exclusão dos produtos como uma operação sem suporte.</span><span class="sxs-lookup"><span data-stu-id="9bc6b-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc6b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bc6b-125">See Also</span></span>  
 [<span data-ttu-id="9bc6b-126">Como: definir uma operação de serviço</span><span class="sxs-lookup"><span data-stu-id="9bc6b-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 <span data-ttu-id="9bc6b-127">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9bc6b-127">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)</span></span>
