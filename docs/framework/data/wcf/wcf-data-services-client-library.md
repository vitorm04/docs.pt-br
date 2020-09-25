---
title: Biblioteca de cliente do WCF Data Services
description: Saiba como usar WCF Data Services bibliotecas de cliente para acessar e alterar dados de um aplicativo cliente .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: d1554dd149e3d447a67cd2ef41aef9042e14fd06
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204353"
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="2e753-103">Biblioteca de cliente do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2e753-103">WCF Data Services Client Library</span></span>

<span data-ttu-id="2e753-104">Qualquer aplicativo pode interagir com um serviço de dados baseado em Protocolo Open Data (OData) se ele puder enviar uma solicitação HTTP e processar o feed OData que um serviço de dados retorna.</span><span class="sxs-lookup"><span data-stu-id="2e753-104">Any application can interact with an Open Data Protocol (OData)-based data service if it can send an HTTP request and process the OData feed that a data service returns.</span></span> <span data-ttu-id="2e753-105">Essa interoperabilidade permite acessar serviços baseados em OData de uma ampla variedade de aplicativos habilitados para a Web.</span><span class="sxs-lookup"><span data-stu-id="2e753-105">This interoperability enables you to access OData-based services from a broad range of Web-enabled applications.</span></span> <span data-ttu-id="2e753-106">A WCF Data Services inclui bibliotecas de cliente que fornecem uma experiência de programação mais rica quando você consome feeds OData de aplicativos baseados em .NET Framework ou Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2e753-106">WCF Data Services includes client libraries that provide a richer programming experience when you consume OData feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="2e753-107">As duas principais classes de biblioteca de cliente são as classes <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601>.</span><span class="sxs-lookup"><span data-stu-id="2e753-107">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="2e753-108">A classe <xref:System.Data.Services.Client.DataServiceContext> encapsula as operações que têm suporte em um serviço de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="2e753-108">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="2e753-109">Embora os serviços OData sejam sem estado, o contexto não é.</span><span class="sxs-lookup"><span data-stu-id="2e753-109">Although OData services are stateless, the context is not.</span></span> <span data-ttu-id="2e753-110">Portanto, você pode usar a <xref:System.Data.Services.Client.DataServiceContext> classe para manter o estado no cliente entre as interações com o serviço de dados para dar suporte a recursos como o gerenciamento de alterações.</span><span class="sxs-lookup"><span data-stu-id="2e753-110">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="2e753-111">Essa classe também gerencia identidades e rastreia alterações.</span><span class="sxs-lookup"><span data-stu-id="2e753-111">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="2e753-112">A classe <xref:System.Data.Services.Client.DataServiceQuery%601> representa uma consulta em um conjunto de entidades específico.</span><span class="sxs-lookup"><span data-stu-id="2e753-112">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="2e753-113">Esta seção descreve como usar bibliotecas de cliente para acessar e modificar dados de um aplicativo cliente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e753-113">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="2e753-114">Para obter mais informações sobre como usar a biblioteca de cliente do WCF Data Services com um aplicativo baseado no Silverlight, consulte [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span><span class="sxs-lookup"><span data-stu-id="2e753-114">For more information about how to use the WCF Data Services client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span></span> <span data-ttu-id="2e753-115">Outras bibliotecas de cliente estão disponíveis para permitir que você consuma um feed OData em outros tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2e753-115">Other client libraries are available that enable you to consume an OData feed in other kinds of applications.</span></span> <span data-ttu-id="2e753-116">Para obter mais informações sobre o SDK do OData, consulte [SDK do OData – código de exemplo](https://www.odata.org/ecosystem/#sdk).</span><span class="sxs-lookup"><span data-stu-id="2e753-116">For more information on OData SDK, see [OData SDK - Sample Code](https://www.odata.org/ecosystem/#sdk).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="2e753-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2e753-117">In This Section</span></span>  

 [<span data-ttu-id="2e753-118">Gerar a biblioteca de clientes do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="2e753-118">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="2e753-119">Descreve como gerar uma biblioteca de cliente e classes de serviço de dados do cliente baseadas em feeds OData.</span><span class="sxs-lookup"><span data-stu-id="2e753-119">Describes how to generate a client library and client data service classes that are based on OData feeds.</span></span>  
  
 [<span data-ttu-id="2e753-120">Consultar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="2e753-120">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="2e753-121">Descreve como consultar um serviço de dados de um aplicativo com base no .NET Framework usando bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e753-121">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="2e753-122">Carregar conteúdo adiado</span><span class="sxs-lookup"><span data-stu-id="2e753-122">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="2e753-123">Descreve como carregar o conteúdo adicional não incluído na resposta da consulta inicial.</span><span class="sxs-lookup"><span data-stu-id="2e753-123">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="2e753-124">Atualizar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="2e753-124">Updating the Data Service</span></span>](updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="2e753-125">Descreve como criar, modificar e excluir entidades e relações usando as bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e753-125">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="2e753-126">Operações assíncronas</span><span class="sxs-lookup"><span data-stu-id="2e753-126">Asynchronous Operations</span></span>](asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="2e753-127">Descreve os recursos fornecidos pelas bibliotecas de cliente para trabalhar com um serviço de dados de uma maneira assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2e753-127">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="2e753-128">Operações de envio em lote</span><span class="sxs-lookup"><span data-stu-id="2e753-128">Batching Operations</span></span>](batching-operations-wcf-data-services.md)  
 <span data-ttu-id="2e753-129">Descreve como enviar várias solicitações para o serviço de dados em um único lote usando as bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e753-129">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="2e753-130">Associar dados a controles</span><span class="sxs-lookup"><span data-stu-id="2e753-130">Binding Data to Controls</span></span>](binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="2e753-131">Descreve como associar controles a um feed OData retornado por um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="2e753-131">Describes how to bind controls to a OData feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="2e753-132">Chamar operações de serviço</span><span class="sxs-lookup"><span data-stu-id="2e753-132">Calling Service Operations</span></span>](calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="2e753-133">Descreve como usar o proxy do cliente de biblioteca para chamar operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e753-133">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="2e753-134">Gerenciar o contexto do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="2e753-134">Managing the Data Service Context</span></span>](managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="2e753-135">Descreve as opções para gerenciar o comportamento da biblioteca de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e753-135">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="2e753-136">Trabalhar com os dados binários</span><span class="sxs-lookup"><span data-stu-id="2e753-136">Working with Binary Data</span></span>](working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="2e753-137">Descreve como acessar e alterar os dados binários retornados pelo serviço de dados como um fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="2e753-137">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e753-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="2e753-138">See also</span></span>

- [<span data-ttu-id="2e753-139">Configurando WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="2e753-139">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="2e753-140">Introdução</span><span class="sxs-lookup"><span data-stu-id="2e753-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
