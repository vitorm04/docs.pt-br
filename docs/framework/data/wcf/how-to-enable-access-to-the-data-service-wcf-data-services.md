---
title: "Como: habilitar o acesso ao serviço de dados (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b41de296143d325ba0e1932831d4a3ef1bd7dc80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="382bc-102">Como: habilitar o acesso ao serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="382bc-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="382bc-103">Em [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você deve conceder explicitamente acesso a recursos que são expostos por um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="382bc-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="382bc-104">Isso significa que, depois de criar um novo serviço de dados, você deve ainda explicitamente fornecer acesso a recursos individuais, como conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="382bc-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="382bc-105">Este tópico mostra como habilitar a leitura e acesso de gravação a cinco da entidade define no serviço de dados Northwind é criado quando você concluir o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="382bc-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="382bc-106">Porque o <xref:System.Data.Services.EntitySetRights> enumeração é definida usando o <xref:System.FlagsAttribute>, você pode usar uma lógica ou conjunto de operador para especificar várias permissões para uma única entidade.</span><span class="sxs-lookup"><span data-stu-id="382bc-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="382bc-107">Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="382bc-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="382bc-108">Em um serviço de dados de produção, para evitar acesso não autorizado aos recursos, você deve também proteger o aplicativo em si.</span><span class="sxs-lookup"><span data-stu-id="382bc-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="382bc-109">Para obter mais informações, consulte [NIB: segurança ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="382bc-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="382bc-110">Para habilitar o acesso ao serviço de dados</span><span class="sxs-lookup"><span data-stu-id="382bc-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="382bc-111">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="382bc-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="382bc-112">Isso permite que os clientes leram e acesso de gravação para o `Orders` e `Order_Details` conjuntos de entidade e acesso somente leitura para o `Customers` conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="382bc-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382bc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="382bc-113">See Also</span></span>  
 [<span data-ttu-id="382bc-114">Como: desenvolver um WCF Data Services em execução no IIS</span><span class="sxs-lookup"><span data-stu-id="382bc-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="382bc-115">Configurando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="382bc-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
