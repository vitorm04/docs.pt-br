---
title: WCF Data Services 4.5
description: Saiba mais sobre WCF Data Services, um componente .NET Framework que dá suporte a serviços para expor e consumir dados usando a semântica REST.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247747"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="c7c3c-103">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="c7c3c-103">WCF Data Services 4.5</span></span>

<span data-ttu-id="c7c3c-104">WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") é um componente da .NET Framework que permite criar serviços que usam o Protocolo Open Data (OData) para expor e consumir dados pela Web ou intranet usando a semântica da [REST (transferência de estado de reapresentação)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span><span class="sxs-lookup"><span data-stu-id="c7c3c-104">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="c7c3c-105">OData expõem dados como recursos que são endereçáveis por URIs.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-105">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="c7c3c-106">Os dados são acessados e alterados usando os verbos HTTP padrão GET, PUT, POST e DELETE.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-106">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="c7c3c-107">O OData usa as convenções de relacionamento de entidade do [modelo de dados de entidade](../adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-107">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="c7c3c-108">WCF Data Services usa o protocolo OData para endereçar e atualizar recursos.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-108">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="c7c3c-109">Dessa forma, você pode acessar esses serviços de qualquer cliente que ofereça suporte a OData.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-109">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="c7c3c-110">O OData permite que você solicite e grave dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões para trocar e atualizar dados como XML e JavaScript Object Notation (JSON), um formato de troca de dados baseado em texto usado extensivamente em aplicativos AJAX.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-110">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="c7c3c-111">WCF Data Services pode expor dados originados de várias fontes como feeds OData.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-111">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="c7c3c-112">As ferramentas do Visual Studio facilitam a criação de um serviço baseado em OData usando um modelo de dados do ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-112">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="c7c3c-113">Você também pode criar feeds OData com base em classes Common Language Runtime (CLR) e até mesmo dados de associação tardia ou não tipada.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-113">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="c7c3c-114">WCF Data Services também inclui um conjunto de bibliotecas de cliente, uma para aplicativos cliente .NET Framework geral e outra especificamente para aplicativos baseados no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-114">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="c7c3c-115">Essas bibliotecas de cliente fornecem um modelo de programação baseado em objeto quando você acessa um feed OData de ambientes como o .NET Framework e o Silverlight.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-115">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="c7c3c-116">Onde devo começar?</span><span class="sxs-lookup"><span data-stu-id="c7c3c-116">Where Should I Start?</span></span>

<span data-ttu-id="c7c3c-117">Dependendo de seus interesses, considere a introdução ao WCF Data Services em um dos tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-117">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="c7c3c-118">Desejo ir diretamente para...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-118">I want to jump right in...</span></span>

- [<span data-ttu-id="c7c3c-119">Início rápido</span><span class="sxs-lookup"><span data-stu-id="c7c3c-119">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-120">Introdução</span><span class="sxs-lookup"><span data-stu-id="c7c3c-120">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="c7c3c-121">Mostrar apenas alguns códigos...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-121">Just show me some code...</span></span>

- [<span data-ttu-id="c7c3c-122">Início rápido</span><span class="sxs-lookup"><span data-stu-id="c7c3c-122">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-123">Como executar consultas de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c7c3c-123">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-124">Como associar dados aos elementos do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="c7c3c-124">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="c7c3c-125">Quero saber mais sobre o OData...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-125">I want to know more about OData...</span></span>

- [<span data-ttu-id="c7c3c-126">White Paper: introdução ao OData</span><span class="sxs-lookup"><span data-stu-id="c7c3c-126">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="c7c3c-127">Protocolo Open Data site</span><span class="sxs-lookup"><span data-stu-id="c7c3c-127">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="c7c3c-128">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="c7c3c-128">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="c7c3c-129">Quero ver exemplos de ponta a ponta...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-129">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="c7c3c-130">[Guia de início rápido WCF Data Services](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="c7c3c-130">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="c7c3c-131">SDK do OData – código de exemplo</span><span class="sxs-lookup"><span data-stu-id="c7c3c-131">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="c7c3c-132">Como ele se integra ao Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="c7c3c-132">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="c7c3c-133">Gerando a biblioteca do cliente de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c7c3c-133">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-134">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c7c3c-134">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="c7c3c-135">Provedor de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c7c3c-135">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="c7c3c-136">O que posso fazer com ele?</span><span class="sxs-lookup"><span data-stu-id="c7c3c-136">What can I do with it?</span></span>

- [<span data-ttu-id="c7c3c-137">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c7c3c-137">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="c7c3c-138">Cenários de aplicativos</span><span class="sxs-lookup"><span data-stu-id="c7c3c-138">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="c7c3c-139">Quero usar LINQ...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-139">I want to use LINQ...</span></span>

- [<span data-ttu-id="c7c3c-140">Consultar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c7c3c-140">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-141">Considerações sobre o LINQ</span><span class="sxs-lookup"><span data-stu-id="c7c3c-141">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="c7c3c-142">Como executar consultas de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c7c3c-142">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="c7c3c-143">Ainda preciso de mais algumas informações...</span><span class="sxs-lookup"><span data-stu-id="c7c3c-143">I still need some more information...</span></span>

- [<span data-ttu-id="c7c3c-144">Blog da equipe do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="c7c3c-144">WCF Data Services Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [<span data-ttu-id="c7c3c-145">Recursos</span><span class="sxs-lookup"><span data-stu-id="c7c3c-145">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="c7c3c-146">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c7c3c-146">In This Section</span></span>

[<span data-ttu-id="c7c3c-147">Visão geral</span><span class="sxs-lookup"><span data-stu-id="c7c3c-147">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="c7c3c-148">Fornece uma visão geral dos recursos e funcionalidades disponíveis no WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-148">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="c7c3c-149">[O que há de novo no WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="c7c3c-149">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="c7c3c-150">Descreve a nova funcionalidade no WCF Data Services e suporte para novos recursos OData.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-150">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="c7c3c-151">Introdução</span><span class="sxs-lookup"><span data-stu-id="c7c3c-151">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="c7c3c-152">Descreve como expor e consumir feeds OData usando WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-152">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="c7c3c-153">Configurando WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="c7c3c-153">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="c7c3c-154">Descreve como criar e configurar um serviço de dados que expõe feeds OData.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-154">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="c7c3c-155">Biblioteca de cliente do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="c7c3c-155">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="c7c3c-156">Descreve como usar bibliotecas de cliente para consumir feeds OData de um aplicativo cliente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7c3c-156">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7c3c-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="c7c3c-157">See also</span></span>

- <span data-ttu-id="c7c3c-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) [REST (Transferência de Estado Representacional)]</span><span class="sxs-lookup"><span data-stu-id="c7c3c-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
