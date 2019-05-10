---
title: Hospeda o serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: bca11c0c1828513077985aa11553ec5c0ad52a27
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910796"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="3ee75-102">Hospeda o serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3ee75-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="3ee75-103">Usando o WCF Data Services, você pode criar um serviço que expõe dados como um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span><span class="sxs-lookup"><span data-stu-id="3ee75-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="3ee75-104">Esse serviço de dados é definido como uma classe que herda de <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="3ee75-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="3ee75-105">Essa classe fornece a funcionalidade necessária para processar mensagens de solicitação, realizar atualizações na fonte de dados e gerar mensagens de respostas, conforme exigido pelo OData.</span><span class="sxs-lookup"><span data-stu-id="3ee75-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="3ee75-106">No entanto, um serviço de dados não é possível associar a e escuta um soquete de rede para solicitações HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="3ee75-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="3ee75-107">Para essa funcionalidade necessária, o serviço de dados se baseia em um componente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="3ee75-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="3ee75-108">O host de serviço de dados executa as seguintes tarefas em nome do serviço de dados:</span><span class="sxs-lookup"><span data-stu-id="3ee75-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="3ee75-109">Escuta as solicitações e encaminha essas solicitações para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="3ee75-110">Cria uma instância do serviço de dados para cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="3ee75-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="3ee75-111">Solicita que o serviço de dados processar a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="3ee75-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="3ee75-112">Envia a resposta em nome do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="3ee75-113">Para simplificar a hospedagem de um serviço de dados, o WCF Data Services foi projetado para integrar com o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ee75-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3ee75-114">O serviço de dados fornece uma implementação de WCF padrão que serve como o host de serviço de dados em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ee75-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="3ee75-115">Portanto, você pode hospedar um serviço de dados em uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="3ee75-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="3ee75-116">Em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ee75-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>

- <span data-ttu-id="3ee75-117">Em um aplicativo gerenciado que oferece suporte aos serviços do WCF auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="3ee75-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="3ee75-118">Em alguns outro host de serviço de dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="3ee75-119">Hospedar um serviço de dados em um aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3ee75-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="3ee75-120">Quando você usa o **Adicionar Novo Item** caixa de diálogo no Visual Studio 2015 para definir um serviço de dados em um aplicativo ASP.NET, a ferramenta gera dois novos arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="3ee75-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="3ee75-121">O primeiro arquivo tem um `.svc` extensão e instrui o tempo de execução do WCF como criar uma instância de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="3ee75-122">A seguir está um exemplo desse arquivo para o serviço de dados de exemplo Northwind criado quando você conclui o [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="3ee75-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="3ee75-123">Essa diretiva diz ao aplicativo para criar o host de serviço para a classe de serviço de dados nomeado usando o <xref:System.Data.Services.DataServiceHostFactory> classe.</span><span class="sxs-lookup"><span data-stu-id="3ee75-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="3ee75-124">A página code-behind para o `.svc` arquivo contém a classe que é a implementação do serviço de dados em si, é definido da seguinte maneira para o serviço de dados de exemplo Northwind:</span><span class="sxs-lookup"><span data-stu-id="3ee75-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="3ee75-125">Como um serviço de dados se comporta como um serviço WCF, o serviço de dados se integra com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] e segue o modelo de programação Web do WCF.</span><span class="sxs-lookup"><span data-stu-id="3ee75-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="3ee75-126">Para obter mais informações, consulte [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) e [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="3ee75-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="3ee75-127">Serviços WCF auto-hospedado</span><span class="sxs-lookup"><span data-stu-id="3ee75-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="3ee75-128">Como ele incorpora uma implementação de WCF, o WCF Data Services oferecem suporte auto-hospedagem em um serviço de dados como um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="3ee75-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="3ee75-129">Um serviço pode ser auto-hospedado em qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo, como um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="3ee75-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="3ee75-130">O <xref:System.Data.Services.DataServiceHost> classe, que herda de <xref:System.ServiceModel.Web.WebServiceHost>, é usado para instanciar o serviço de dados em um endereço específico.</span><span class="sxs-lookup"><span data-stu-id="3ee75-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="3ee75-131">Hospedagem interna pode ser usada para desenvolvimento e teste, pois isso pode tornar mais fácil de implantar e solucionar problemas do serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee75-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="3ee75-132">No entanto, esse tipo de hospedagem não fornece recursos de hospedagem e gerenciamento avançados fornecidos pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ou pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="3ee75-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="3ee75-133">Para obter mais informações, consulte [hospedagem em um aplicativo gerenciado](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="3ee75-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="3ee75-134">Definindo um Host de serviço de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="3ee75-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="3ee75-135">Para casos em que a implementação de host do WCF é restritiva demais, você também pode definir um host personalizado para um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="3ee75-136">Qualquer classe que implemente <xref:System.Data.Services.IDataServiceHost> interface pode ser usada como o host de rede para um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="3ee75-137">Um host personalizado deve implementar a <xref:System.Data.Services.IDataServiceHost> de interface e ser capaz de lidar com as seguintes responsabilidades básicas do host do serviço de dados:</span><span class="sxs-lookup"><span data-stu-id="3ee75-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="3ee75-138">Fornece o serviço de dados com o caminho raiz do serviço.</span><span class="sxs-lookup"><span data-stu-id="3ee75-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="3ee75-139">Processar informações de cabeçalhos de solicitação e resposta ao apropriado <xref:System.Data.Services.IDataServiceHost> implementação de membro.</span><span class="sxs-lookup"><span data-stu-id="3ee75-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="3ee75-140">Trate as exceções geradas pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="3ee75-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="3ee75-141">Valide parâmetros na cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="3ee75-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee75-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ee75-142">See also</span></span>

- <span data-ttu-id="3ee75-143">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3ee75-143">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)</span></span>
- [<span data-ttu-id="3ee75-144">Expondo seus dados como um serviço</span><span class="sxs-lookup"><span data-stu-id="3ee75-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="3ee75-145">Configurando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="3ee75-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
