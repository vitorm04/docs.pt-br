---
title: Interceptores (WCF Data Services)
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
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7aad516b819723c97a40a016a46ddcbe0fcdf4d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="ec2d6-102">Interceptores (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ec2d6-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="ec2d6-103">permite que um aplicativo interceptar mensagens de solicitação para que você possa adicionar lógica personalizada para uma operação.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-103"> enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="ec2d6-104">Você pode usar essa lógica personalizada para validar dados em mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="ec2d6-105">Você também pode usá-la para restringir mais o escopo de uma solicitação de consulta, como inserir uma política de autorização personalizada com base na solicitação.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="ec2d6-106">A interceptação é executada por métodos especialmente atribuídos no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="ec2d6-107">Esses métodos são chamados pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] no ponto apropriado no processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="ec2d6-108">Interceptores são definidos em uma base de conjunto por entidade e métodos interceptador não podem aceitar parâmetros da solicitação pode ser operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="ec2d6-109">Métodos de interceptador de consulta, que são chamados durante o processamento de uma solicitação HTTP GET, devem retornar uma expressão lambda que determina se uma instância da entidade do interceptador definida deve ser retornada pelos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="ec2d6-110">Esta expressão é usada pelo serviço de dados para refinar mais a operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="ec2d6-111">Veja a seguir um exemplo de definição de um interceptor de consulta.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="ec2d6-112">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ec2d6-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ec2d6-113">Os interceptores de alteração, que são chamados para processar operações sem consulta, devem retornar `void` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ec2d6-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="ec2d6-114">Os métodos de interceptor de alteração devem aceitar estes dois parâmetros:</span><span class="sxs-lookup"><span data-stu-id="ec2d6-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1.  <span data-ttu-id="ec2d6-115">Um parâmetro de um tipo que seja compatível com o tipo de entidade do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="ec2d6-116">Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá as informações de entidade enviadas pela solicitação.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2.  <span data-ttu-id="ec2d6-117">Um parâmetro do tipo <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="ec2d6-118">Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá a operação que a solicitação estiver tentando executar.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="ec2d6-119">Veja a seguir um exemplo de definição de um interceptor de alteração.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="ec2d6-120">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ec2d6-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ec2d6-121">Os atributos a seguir têm suporte para interceptação.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="ec2d6-122">**[QueryInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="ec2d6-122">**[QueryInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="ec2d6-123">Os métodos com o atributo <xref:System.Data.Services.QueryInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP GET é recebida para o recurso de destino do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="ec2d6-124">Esses métodos devem sempre retornar uma expressão lambda no formato `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="ec2d6-125">**[ChangeInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="ec2d6-125">**[ChangeInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="ec2d6-126">Os métodos com o atributo <xref:System.Data.Services.ChangeInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP, que não seja HTTP GET, é recebida para o recurso de destino do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ec2d6-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="ec2d6-127">Esses métodos devem sempre retornar `void` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ec2d6-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="ec2d6-128">Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ec2d6-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2d6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec2d6-129">See Also</span></span>  
 [<span data-ttu-id="ec2d6-130">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="ec2d6-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
