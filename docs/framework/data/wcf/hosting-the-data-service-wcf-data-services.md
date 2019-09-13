---
title: Hospedando o serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 15122984dbaf3245436ff21836065c05131f71d1
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894320"
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="64555-102">Hospedando o serviço de dados (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="64555-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="64555-103">Usando WCF Data Services, você pode criar um serviço que expõe dados como um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span><span class="sxs-lookup"><span data-stu-id="64555-103">By using WCF Data Services, you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="64555-104">Esse serviço de dados é definido como uma classe que herda <xref:System.Data.Services.DataService%601>de.</span><span class="sxs-lookup"><span data-stu-id="64555-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="64555-105">Essa classe fornece a funcionalidade necessária para processar mensagens de solicitação, executar atualizações na fonte de dados e gerar mensagens de respostas, conforme exigido pelo OData.</span><span class="sxs-lookup"><span data-stu-id="64555-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by OData.</span></span> <span data-ttu-id="64555-106">No entanto, um serviço de dados não pode se associar a e escutar em um soquete de rede para solicitações HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="64555-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="64555-107">Para essa funcionalidade necessária, o serviço de dados depende de um componente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="64555-107">For this required functionality, the data service relies on a hosting component.</span></span>

 <span data-ttu-id="64555-108">O host do serviço de dados executa as seguintes tarefas em nome do serviço de dados:</span><span class="sxs-lookup"><span data-stu-id="64555-108">The data service host performs the following tasks on behalf of the data service:</span></span>

- <span data-ttu-id="64555-109">Escuta solicitações e roteia essas solicitações para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-109">Listens for requests and routes these requests to the data service.</span></span>

- <span data-ttu-id="64555-110">Cria uma instância do serviço de dados para cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="64555-110">Creates an instance of the data service for each request.</span></span>

- <span data-ttu-id="64555-111">Solicita que o serviço de dados processe a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="64555-111">Requests that the data service process the incoming request.</span></span>

- <span data-ttu-id="64555-112">Envia a resposta em nome do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-112">Sends the response on behalf of the data service.</span></span>

 <span data-ttu-id="64555-113">Para simplificar a hospedagem de um serviço de dados, WCF Data Services é projetada para integrar com o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="64555-113">To simplify hosting a data service, WCF Data Services is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="64555-114">O serviço de dados fornece uma implementação padrão do WCF que serve como o host do serviço de dados em um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64555-114">The data service provides a default WCF implementation that serves as the data service host in an ASP.NET application.</span></span> <span data-ttu-id="64555-115">Portanto, você pode hospedar um serviço de dados do de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="64555-115">Therefore, you can host a data service in one of the following ways:</span></span>

- <span data-ttu-id="64555-116">Em um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64555-116">In an ASP.NET application.</span></span>

- <span data-ttu-id="64555-117">Em um aplicativo gerenciado que dá suporte a serviços WCF hospedados internamente.</span><span class="sxs-lookup"><span data-stu-id="64555-117">In a managed application that supports self-hosted WCF services.</span></span>

- <span data-ttu-id="64555-118">Em algum outro host de serviço de dados personalizado.</span><span class="sxs-lookup"><span data-stu-id="64555-118">In some other custom data service host.</span></span>

## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="64555-119">Hospedando um serviço de dados em um aplicativo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="64555-119">Hosting a Data Service in an ASP.NET Application</span></span>

<span data-ttu-id="64555-120">Quando você usa a caixa de diálogo **Adicionar novo item** no Visual Studio 2015 para definir um serviço de dados em um aplicativo ASP.net, a ferramenta gera dois novos arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="64555-120">When you use the **Add New Item** dialog in Visual Studio 2015 to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="64555-121">O primeiro arquivo tem uma `.svc` extensão e instrui o tempo de execução do WCF a criar uma instância do serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="64555-122">Este é um exemplo desse arquivo para o serviço de dados de exemplo Northwind criado quando você conclui o [início rápido](quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="64555-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](quickstart-wcf-data-services.md):</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 <span data-ttu-id="64555-123">Essa diretiva informa o aplicativo para criar o host de serviço para a classe de serviço de dados nomeada <xref:System.Data.Services.DataServiceHostFactory> usando a classe.</span><span class="sxs-lookup"><span data-stu-id="64555-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>

 <span data-ttu-id="64555-124">A página code-behind do `.svc` arquivo contém a classe que é a implementação do próprio serviço de dados, que é definida da seguinte maneira para o serviço de dados de exemplo Northwind:</span><span class="sxs-lookup"><span data-stu-id="64555-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 <span data-ttu-id="64555-125">Como um serviço de dados se comporta como um serviço WCF, o serviço de dados integra-se ao ASP.NET e segue o modelo de programação Web do WCF.</span><span class="sxs-lookup"><span data-stu-id="64555-125">Because a data service behaves like a WCF service, the data service integrates with ASP.NET and follows the WCF Web programming model.</span></span> <span data-ttu-id="64555-126">Para obter mais informações, consulte [Serviços WCF e](../../wcf/feature-details/wcf-services-and-aspnet.md) [modelo de programação Web http](../../wcf/feature-details/wcf-web-http-programming-model.md)do ASP.net e WCF.</span><span class="sxs-lookup"><span data-stu-id="64555-126">For more information, see [WCF Services and ASP.NET](../../wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../wcf/feature-details/wcf-web-http-programming-model.md).</span></span>

## <a name="self-hosted-wcf-services"></a><span data-ttu-id="64555-127">Serviços WCF auto-hospedados</span><span class="sxs-lookup"><span data-stu-id="64555-127">Self-Hosted WCF Services</span></span>
 <span data-ttu-id="64555-128">Como ele incorpora uma implementação do WCF, WCF Data Services dá suporte à hospedagem interna de um serviço de dados como um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="64555-128">Because it incorporates a WCF implementation, WCF Data Services support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="64555-129">Um serviço pode ser hospedado automaticamente em qualquer aplicativo .NET Framework, como um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="64555-129">A service can be self-hosted in any .NET Framework application, such as a console application.</span></span> <span data-ttu-id="64555-130">A <xref:System.Data.Services.DataServiceHost> classe, que é herdada de <xref:System.ServiceModel.Web.WebServiceHost>, é usada para instanciar o serviço de dados em um endereço específico.</span><span class="sxs-lookup"><span data-stu-id="64555-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>

 <span data-ttu-id="64555-131">A hospedagem interna pode ser usada para desenvolvimento e teste porque pode facilitar a implantação e a solução de problemas do serviço.</span><span class="sxs-lookup"><span data-stu-id="64555-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="64555-132">No entanto, esse tipo de hospedagem não fornece recursos avançados de hospedagem e gerenciamento fornecidos pelo ASP.NET ou pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="64555-132">However, this kind of hosting does not provide the advanced hosting and management features provided by ASP.NET or by Internet Information Services (IIS).</span></span> <span data-ttu-id="64555-133">Para obter mais informações, consulte [hospedagem em um aplicativo gerenciado](../../wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="64555-133">For more information, see [Hosting in a Managed Application](../../wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="64555-134">Definindo um host de serviço de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="64555-134">Defining a Custom Data Service Host</span></span>
 <span data-ttu-id="64555-135">Para casos em que a implementação do host do WCF é muito restritiva, você também pode definir um host personalizado para um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="64555-136">Qualquer classe que implemente <xref:System.Data.Services.IDataServiceHost> a interface pode ser usada como o host de rede para um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="64555-137">Um host personalizado deve implementar a <xref:System.Data.Services.IDataServiceHost> interface e ser capaz de lidar com as seguintes responsabilidades básicas do host do serviço de dados:</span><span class="sxs-lookup"><span data-stu-id="64555-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>

- <span data-ttu-id="64555-138">Forneça o serviço de dados com o caminho raiz do serviço.</span><span class="sxs-lookup"><span data-stu-id="64555-138">Provide the data service with the service root path.</span></span>

- <span data-ttu-id="64555-139">Processar informações de cabeçalhos de solicitação e resposta para <xref:System.Data.Services.IDataServiceHost> a implementação de membro apropriada.</span><span class="sxs-lookup"><span data-stu-id="64555-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>

- <span data-ttu-id="64555-140">Tratar exceções geradas pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="64555-140">Handle exceptions raised by the data service.</span></span>

- <span data-ttu-id="64555-141">Valide os parâmetros na cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="64555-141">Validate parameters in the query string.</span></span>

## <a name="see-also"></a><span data-ttu-id="64555-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64555-142">See also</span></span>

- <span data-ttu-id="64555-143">[Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="64555-143">[Defining WCF Data Services](defining-wcf-data-services.md)</span></span>
- [<span data-ttu-id="64555-144">Expondo seus dados como um serviço</span><span class="sxs-lookup"><span data-stu-id="64555-144">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
- [<span data-ttu-id="64555-145">Configurando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="64555-145">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
