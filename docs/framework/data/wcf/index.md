---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: aace683b1a105445b5a3ba3de0a6a671859588b5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937438"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="3fc8c-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="3fc8c-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="3fc8c-103">WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") é um componente da .NET Framework que permite criar serviços que usam o Protocolo Open Data (OData) para expor e consumir dados pela Web ou intranet usando a semântica da [REST (transferência de estado de reapresentação)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="3fc8c-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="3fc8c-104">OData expõe dados como recursos endereçáveis por URIs.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="3fc8c-105">Os dados são acessados e modificados usando verbos HTTP padrão, que são GET, PUT, POST e DELETE.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="3fc8c-106">O OData usa as convenções de relacionamento de entidade do [modelo de dados de entidade](../adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-106">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="3fc8c-107">WCF Data Services usa o protocolo OData para endereçar e atualizar recursos.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="3fc8c-108">Dessa forma, você pode acessar esses serviços de qualquer cliente que ofereça suporte a OData.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="3fc8c-109">O OData permite que você solicite e grave dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões para a troca e atualização de dados como XML e JavaScript Object Notation (JSON), um formato de troca de dados baseado em texto usado extensivamente no AJAX aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="3fc8c-110">WCF Data Services pode expor dados originados de várias fontes como feeds OData.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="3fc8c-111">As ferramentas do Visual Studio facilitam a criação de um serviço baseado em OData usando um modelo de dados do ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="3fc8c-112">Você também pode criar feeds OData com base em classes Common Language Runtime (CLR) e até mesmo dados de associação tardia ou não tipada.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="3fc8c-113">WCF Data Services também inclui um conjunto de bibliotecas de cliente, uma para aplicativos cliente .NET Framework geral e outra especificamente para aplicativos baseados no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="3fc8c-114">Essas bibliotecas de cliente fornecem um modelo de programação baseado em objeto quando você acessa um feed OData de ambientes como o .NET Framework e o Silverlight.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="3fc8c-115">Onde devo começar?</span><span class="sxs-lookup"><span data-stu-id="3fc8c-115">Where Should I Start?</span></span>

<span data-ttu-id="3fc8c-116">Dependendo de seus interesses, considere a introdução ao WCF Data Services em um dos tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="3fc8c-117">Desejo ir diretamente para...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-117">I want to jump right in...</span></span>

- <span data-ttu-id="3fc8c-118">[Quickstart](quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-118">[Quickstart](quickstart-wcf-data-services.md)</span></span>

- [<span data-ttu-id="3fc8c-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="3fc8c-119">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="3fc8c-120">Mostrar apenas alguns códigos...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-120">Just show me some code...</span></span>

- <span data-ttu-id="3fc8c-121">[Quickstart](quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-121">[Quickstart](quickstart-wcf-data-services.md)</span></span>

- <span data-ttu-id="3fc8c-122">[How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-122">[How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md)</span></span>

- <span data-ttu-id="3fc8c-123">[How to: Bind Data to Windows Presentation Foundation Elements](bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-123">[How to: Bind Data to Windows Presentation Foundation Elements](bind-data-to-wpf-elements-wcf-data-services.md)</span></span>

<span data-ttu-id="3fc8c-124">Quero saber mais sobre o OData...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-124">I want to know more about OData...</span></span>

- [<span data-ttu-id="3fc8c-125">White Paper: introdução ao OData</span><span class="sxs-lookup"><span data-stu-id="3fc8c-125">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="3fc8c-126">Protocolo Open Data site</span><span class="sxs-lookup"><span data-stu-id="3fc8c-126">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="3fc8c-127">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="3fc8c-127">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="3fc8c-128">Quero ver exemplos de ponta a ponta...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-128">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="3fc8c-129">[Guia de início rápido WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="3fc8c-129">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="3fc8c-130">SDK do OData – código de exemplo</span><span class="sxs-lookup"><span data-stu-id="3fc8c-130">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="3fc8c-131">Como ele se integra ao Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="3fc8c-131">How does it integrate with Visual Studio?</span></span>

- <span data-ttu-id="3fc8c-132">[Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-132">[Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md)</span></span>

- <span data-ttu-id="3fc8c-133">[Creating the Data Service](creating-the-data-service.md) (Criando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-133">[Creating the Data Service](creating-the-data-service.md)</span></span>

- <span data-ttu-id="3fc8c-134">[Entity Framework Provider](entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-134">[Entity Framework Provider](entity-framework-provider-wcf-data-services.md)</span></span>

<span data-ttu-id="3fc8c-135">O que posso fazer com ele?</span><span class="sxs-lookup"><span data-stu-id="3fc8c-135">What can I do with it?</span></span>

- [<span data-ttu-id="3fc8c-136">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="3fc8c-136">Overview</span></span>](wcf-data-services-overview.md)

- <span data-ttu-id="3fc8c-137">[Application Scenarios](application-scenarios-wcf-data-services.md) (Cenários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-137">[Application Scenarios](application-scenarios-wcf-data-services.md)</span></span>

<span data-ttu-id="3fc8c-138">Quero usar LINQ...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-138">I want to use LINQ...</span></span>

- <span data-ttu-id="3fc8c-139">[Querying the Data Service](querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-139">[Querying the Data Service](querying-the-data-service-wcf-data-services.md)</span></span>

- <span data-ttu-id="3fc8c-140">[LINQ Considerations](linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-140">[LINQ Considerations](linq-considerations-wcf-data-services.md)</span></span>

- <span data-ttu-id="3fc8c-141">[How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-141">[How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md)</span></span>

<span data-ttu-id="3fc8c-142">Ainda preciso de mais algumas informações...</span><span class="sxs-lookup"><span data-stu-id="3fc8c-142">I still need some more information...</span></span>

- [<span data-ttu-id="3fc8c-143">Blog da equipe do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="3fc8c-143">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="3fc8c-144">Recursos</span><span class="sxs-lookup"><span data-stu-id="3fc8c-144">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="3fc8c-145">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3fc8c-145">In This Section</span></span>

[<span data-ttu-id="3fc8c-146">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="3fc8c-146">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="3fc8c-147">Fornece uma visão geral dos recursos e funcionalidades disponíveis no WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-147">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="3fc8c-148">[O que há de novo no WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="3fc8c-148">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="3fc8c-149">Descreve a nova funcionalidade no WCF Data Services e suporte para novos recursos OData.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-149">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="3fc8c-150">Introdução</span><span class="sxs-lookup"><span data-stu-id="3fc8c-150">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="3fc8c-151">Descreve como expor e consumir feeds OData usando WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-151">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

<span data-ttu-id="3fc8c-152">[Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-152">[Defining WCF Data Services](defining-wcf-data-services.md)</span></span>

<span data-ttu-id="3fc8c-153">Descreve como criar e configurar um serviço de dados que expõe feeds OData.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-153">Describes how to create and configure a data service that exposes OData feeds.</span></span>

<span data-ttu-id="3fc8c-154">[WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3fc8c-154">[WCF Data Services Client Library](wcf-data-services-client-library.md)</span></span>

<span data-ttu-id="3fc8c-155">Descreve como usar bibliotecas de cliente para consumir feeds OData de um aplicativo cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3fc8c-155">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fc8c-156">Veja também</span><span class="sxs-lookup"><span data-stu-id="3fc8c-156">See also</span></span>

- <span data-ttu-id="3fc8c-157">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) [REST (Transferência de Estado Representacional)]</span><span class="sxs-lookup"><span data-stu-id="3fc8c-157">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
