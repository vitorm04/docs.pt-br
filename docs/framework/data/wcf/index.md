---
title: WCF Data Services 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5b27a51dcec17f72b86e77a7ee2ab773aec1dc3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="5dc67-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="5dc67-102">WCF Data Services 4.5</span></span>
<span data-ttu-id="5dc67-103">O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (anteriormente conhecido como "ADO.NET Data Services") é um componente do .NET Framework que permite criar serviços que usam o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor e consumir dados na Web ou na intranet usando a semântica de [REST (Transferência de Estado Representacional)](http://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="5dc67-103">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="5dc67-104">O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expõe dados como recursos endereçáveis por URIs.</span><span class="sxs-lookup"><span data-stu-id="5dc67-104">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="5dc67-105">Os dados são acessados e alterados usando os verbos HTTP padrão GET, PUT, POST e DELETE.</span><span class="sxs-lookup"><span data-stu-id="5dc67-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="5dc67-106">O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usa as convenções de relacionamento de entidade do [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.</span><span class="sxs-lookup"><span data-stu-id="5dc67-106">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 <span data-ttu-id="5dc67-107">O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usa o protocolo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] para endereçar e atualizar recursos.</span><span class="sxs-lookup"><span data-stu-id="5dc67-107">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="5dc67-108">Assim, é possível acessar esses serviços de qualquer cliente que dê suporte a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="5dc67-109">O [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] permite solicitar e gravar dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões de troca e atualização de dados como XML, e JSON (JavaScript Object Notation), um formato de troca de dados baseado em texto usado extensivamente em aplicativos AJAX.</span><span class="sxs-lookup"><span data-stu-id="5dc67-109">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 <span data-ttu-id="5dc67-110">O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pode expor os dados originados de várias fontes como feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-110">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="5dc67-111">As ferramentas do Visual Studio facilitam a criação de um serviço baseado em [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] por meio de um modelo de dados Entity Framework do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="5dc67-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="5dc67-112">Você também pode criar feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] com base em classes CLR (Common Language Runtime) e até mesmo dados de associação tardia ou não tipados.</span><span class="sxs-lookup"><span data-stu-id="5dc67-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 <span data-ttu-id="5dc67-113">O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também inclui um conjunto de bibliotecas cliente, um para aplicativos cliente .NET Framework gerais e outro especificamente para aplicativos baseados no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="5dc67-113">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="5dc67-114">Essas bibliotecas de clientes fornecem um modelo de programação baseado em objeto quando você acessa um feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de ambientes como o .NET Framework e o Silverlight.</span><span class="sxs-lookup"><span data-stu-id="5dc67-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="5dc67-115">Onde devo começar?</span><span class="sxs-lookup"><span data-stu-id="5dc67-115">Where Should I Start?</span></span>  
 <span data-ttu-id="5dc67-116">Dependendo dos seus interesses, comece pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] em um dos tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5dc67-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="5dc67-117">Desejo ir diretamente para…</span><span class="sxs-lookup"><span data-stu-id="5dc67-117">I want to jump right in…</span></span>  
 -   <span data-ttu-id="5dc67-118">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="5dc67-118">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>  
  
-   [<span data-ttu-id="5dc67-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="5dc67-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   <span data-ttu-id="5dc67-120">[Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)</span><span class="sxs-lookup"><span data-stu-id="5dc67-120">[Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782)</span></span>  
  
-   <span data-ttu-id="5dc67-121">[Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)</span><span class="sxs-lookup"><span data-stu-id="5dc67-121">[Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535)</span></span>  
  
 <span data-ttu-id="5dc67-122">Mostre-me apenas algum código…</span><span class="sxs-lookup"><span data-stu-id="5dc67-122">Just show me some code…</span></span>  
 -   <span data-ttu-id="5dc67-123">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="5dc67-123">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>  
  
-   <span data-ttu-id="5dc67-124">[How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="5dc67-124">[How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)</span></span>  
  
-   <span data-ttu-id="5dc67-125">[How to: Bind Data to Windows Presentation Foundation Elements](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="5dc67-125">[How to: Bind Data to Windows Presentation Foundation Elements](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)</span></span>  
  
 <span data-ttu-id="5dc67-126">Desejo saber mais sobre [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span><span class="sxs-lookup"><span data-stu-id="5dc67-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   <span data-ttu-id="5dc67-127">[Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)</span><span class="sxs-lookup"><span data-stu-id="5dc67-127">[Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867)</span></span>  
  
-   [<span data-ttu-id="5dc67-128">Site do Protocolo Open Data</span><span class="sxs-lookup"><span data-stu-id="5dc67-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="5dc67-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="5dc67-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   <span data-ttu-id="5dc67-130">[OData: Frequently Asked Questions](http://go.microsoft.com/fwlink/?LinkId=185867) (OData: perguntas frequentes)</span><span class="sxs-lookup"><span data-stu-id="5dc67-130">[OData: Frequently Asked Questions](http://go.microsoft.com/fwlink/?LinkId=185867)</span></span>  
  
 <span data-ttu-id="5dc67-131">Desejo assistir a alguns vídeos…</span><span class="sxs-lookup"><span data-stu-id="5dc67-131">I want to watch some videos…</span></span>  
 -   <span data-ttu-id="5dc67-132">[Beginner's Guide to WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220864) (Guia do iniciante do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-132">[Beginner's Guide to WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220864)</span></span>  
  
-   <span data-ttu-id="5dc67-133">[WCF Data Services Developer Videos](http://go.microsoft.com/fwlink/?LinkId=220861) (Vídeos para desenvolvedores do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-133">[WCF Data Services Developer Videos](http://go.microsoft.com/fwlink/?LinkId=220861)</span></span>  
  
-   <span data-ttu-id="5dc67-134">[OData: Developers Web site](http://go.microsoft.com/fwlink/?LinkId=185866) (OData: site para desenvolvedores)</span><span class="sxs-lookup"><span data-stu-id="5dc67-134">[OData: Developers Web site](http://go.microsoft.com/fwlink/?LinkId=185866)</span></span>  
  
 <span data-ttu-id="5dc67-135">Desejo ver exemplos completos</span><span class="sxs-lookup"><span data-stu-id="5dc67-135">I want to see end-to-end samples</span></span>  
 -   <span data-ttu-id="5dc67-136">[WCF Data Services Documentation Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkID=220865) (Amostras de documentação do WCF Data Services na galeria de amostras do MSDN)</span><span class="sxs-lookup"><span data-stu-id="5dc67-136">[WCF Data Services Documentation Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkID=220865)</span></span>  
  
-   <span data-ttu-id="5dc67-137">[Other WCF Data Services Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkId=220866) (Outras amostras do WCF Data Services na galeria de amostras do MSDN)</span><span class="sxs-lookup"><span data-stu-id="5dc67-137">[Other WCF Data Services Samples on MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkId=220866)</span></span>  
  
-   [<span data-ttu-id="5dc67-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="5dc67-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="5dc67-139">Como ele se integra ao Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="5dc67-139">How does it integrate with Visual Studio?</span></span>  
 -   <span data-ttu-id="5dc67-140">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="5dc67-140">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)</span></span>  
  
-   <span data-ttu-id="5dc67-141">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md) (Criando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="5dc67-141">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md)</span></span>  
  
-   <span data-ttu-id="5dc67-142">[Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="5dc67-142">[Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)</span></span>  
  
 <span data-ttu-id="5dc67-143">O que posso fazer com ele?</span><span class="sxs-lookup"><span data-stu-id="5dc67-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="5dc67-144">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="5dc67-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   <span data-ttu-id="5dc67-145">[Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867) (White paper: Introdução ao OData)</span><span class="sxs-lookup"><span data-stu-id="5dc67-145">[Whitepaper: Introducing OData](http://go.microsoft.com/fwlink/?LinkId=220867)</span></span>  
  
-   <span data-ttu-id="5dc67-146">[Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md) (Cenários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="5dc67-146">[Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)</span></span>  
  
 <span data-ttu-id="5dc67-147">Desejo usar o Silverlight…</span><span class="sxs-lookup"><span data-stu-id="5dc67-147">I want to use Silverlight…</span></span>  
 -   <span data-ttu-id="5dc67-148">[Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)</span><span class="sxs-lookup"><span data-stu-id="5dc67-148">[Silverlight Quickstart](http://go.microsoft.com/fwlink/?LinkID=192782)</span></span>  
  
-   [<span data-ttu-id="5dc67-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="5dc67-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   <span data-ttu-id="5dc67-150">[Getting Started with Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366) (Introdução ao Silverlight)</span><span class="sxs-lookup"><span data-stu-id="5dc67-150">[Getting Started with Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366)</span></span>  
  
 <span data-ttu-id="5dc67-151">Desejo criar um aplicativo para Windows Phone…</span><span class="sxs-lookup"><span data-stu-id="5dc67-151">I want to create a Windows Phone application…</span></span>  
 -   <span data-ttu-id="5dc67-152">[Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)</span><span class="sxs-lookup"><span data-stu-id="5dc67-152">[Silverlight Quickstart for Windows Phone Development](http://go.microsoft.com/fwlink/?LinkID=214535)</span></span>  
  
-   <span data-ttu-id="5dc67-153">[Open Data Protocol () Client for Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749) [Cliente do OData (Open Data Protocol) para Windows Phone]</span><span class="sxs-lookup"><span data-stu-id="5dc67-153">[Open Data Protocol (OData) Client for Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749)</span></span>  
  
 <span data-ttu-id="5dc67-154">Desejo usar LINQ…</span><span class="sxs-lookup"><span data-stu-id="5dc67-154">I want to use LINQ…</span></span>  
 -   <span data-ttu-id="5dc67-155">[Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="5dc67-155">[Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)</span></span>  
  
-   <span data-ttu-id="5dc67-156">[LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)</span><span class="sxs-lookup"><span data-stu-id="5dc67-156">[LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)</span></span>  
  
-   <span data-ttu-id="5dc67-157">[How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md) (Como executar consultas de serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="5dc67-157">[How to: Execute Data Service Queries](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)</span></span>  
  
 <span data-ttu-id="5dc67-158">Ainda preciso de mais informações…</span><span class="sxs-lookup"><span data-stu-id="5dc67-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="5dc67-159">Blog da equipe do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="5dc67-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="5dc67-160">Recursos</span><span class="sxs-lookup"><span data-stu-id="5dc67-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   <span data-ttu-id="5dc67-161">[WCF Data Services Developer Center](http://go.microsoft.com/fwlink/?LinkId=220868) (Central de desenvolvedores do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-161">[WCF Data Services Developer Center](http://go.microsoft.com/fwlink/?LinkId=220868)</span></span>  
  
-   [<span data-ttu-id="5dc67-162">Site do Protocolo Open Data</span><span class="sxs-lookup"><span data-stu-id="5dc67-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="5dc67-163">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5dc67-163">In This Section</span></span>  
 [<span data-ttu-id="5dc67-164">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="5dc67-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="5dc67-165">Apresenta uma visão geral dos recursos e da funcionalidade disponíveis no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 <span data-ttu-id="5dc67-166">[What's New in WCF Data Services](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8) (Novidades no WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-166">[What's New in WCF Data Services](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)</span></span>  
 <span data-ttu-id="5dc67-167">Descreve as novas funcionalidades no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] e o suporte para novos recursos do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="5dc67-168">Introdução</span><span class="sxs-lookup"><span data-stu-id="5dc67-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="5dc67-169">Descreve como expor e consumir feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 <span data-ttu-id="5dc67-170">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-170">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)</span></span>  
 <span data-ttu-id="5dc67-171">Descreve como criar e configurar um serviço de dados que expõe feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dc67-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 <span data-ttu-id="5dc67-172">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="5dc67-172">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)</span></span>  
 <span data-ttu-id="5dc67-173">Descreve como usar bibliotecas de clientes para consumir feeds [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de um aplicativo de cliente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dc67-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc67-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dc67-174">See Also</span></span>  
 <span data-ttu-id="5dc67-175">[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]</span><span class="sxs-lookup"><span data-stu-id="5dc67-175">[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)</span></span>
