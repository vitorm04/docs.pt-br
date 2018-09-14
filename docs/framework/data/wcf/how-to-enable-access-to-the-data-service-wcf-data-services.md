---
title: 'Como: habilitar o acesso ao serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: eb9d7cd8e62a73f49fd2b0f2fc2572b01109553b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778533"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="c05d6-102">Como: habilitar o acesso ao serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c05d6-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="c05d6-103">No [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], você deve conceder explicitamente acesso aos recursos que são expostos por um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="c05d6-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="c05d6-104">Isso significa que, depois de criar um novo serviço de dados, você deve explicitamente ainda fornecer acesso aos recursos individuais, como conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="c05d6-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="c05d6-105">Este tópico mostra como habilitar a leitura e acesso de gravação para cinco da entidade define no serviço de dados Northwind é criado quando você conclui o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c05d6-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="c05d6-106">Porque o <xref:System.Data.Services.EntitySetRights> enumeração é definida usando o <xref:System.FlagsAttribute>, você pode usar uma lógica ou operador para especificar várias permissões para uma única entidade definida.</span><span class="sxs-lookup"><span data-stu-id="c05d6-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c05d6-107">Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="c05d6-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="c05d6-108">Em um serviço de dados de produção, para evitar acesso não autorizado aos recursos, você deve também proteger o próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c05d6-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="c05d6-109">Para obter mais informações, consulte [NIB: segurança do ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="c05d6-109">For more information, see [NIB: ASP.NET Security](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="c05d6-110">Para habilitar o acesso ao serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c05d6-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="c05d6-111">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="c05d6-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="c05d6-112">Isso permite que os clientes tenha de leitura e acesso de gravação para o `Orders` e `Order_Details` conjuntos de entidades e acesso somente leitura para o `Customers` conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="c05d6-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05d6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c05d6-113">See Also</span></span>  
 [<span data-ttu-id="c05d6-114">Como desenvolver um WCF Data Service em execução no IIS</span><span class="sxs-lookup"><span data-stu-id="c05d6-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="c05d6-115">Configurando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c05d6-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
