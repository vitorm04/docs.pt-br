---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
  - Astoria
  - 'WCF Data Services, getting started'
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
---

# <a name="wcf-data-services-45"></a><span data-ttu-id="ecd09-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="ecd09-102">WCF Data Services 4.5</span></span>

<span data-ttu-id="ecd09-103">WCF Data Services (anteriormente conhecido como "ADO.NET Data Services") é um componente do .NET Framework que permite que você crie serviços que usam o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] para expor e consumir dados na Web ou intranet usando a semântica de [ transferência de estado representacional (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span><span class="sxs-lookup"><span data-stu-id="ecd09-103">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919).</span></span> <span data-ttu-id="ecd09-104">OData expõem dados como recursos que são endereçáveis por URIs.</span><span class="sxs-lookup"><span data-stu-id="ecd09-104">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="ecd09-105">Os dados são acessados e alterados usando os verbos HTTP padrão GET, PUT, POST e DELETE.</span><span class="sxs-lookup"><span data-stu-id="ecd09-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="ecd09-106">OData usa as convenções de relacionamento entre entidades do [modelo de dados de entidade](../../../../docs/framework/data/adonet/entity-data-model.md) para expor recursos como conjuntos de entidades relacionadas por associações.</span><span class="sxs-lookup"><span data-stu-id="ecd09-106">OData uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="ecd09-107">WCF Data Services usa o protocolo OData para endereçamento e atualização de recursos.</span><span class="sxs-lookup"><span data-stu-id="ecd09-107">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="ecd09-108">Dessa forma, você pode acessar esses serviços de qualquer cliente que dê suporte a OData.</span><span class="sxs-lookup"><span data-stu-id="ecd09-108">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="ecd09-109">OData lhe permite solicitar e gravar dados em recursos usando formatos de transferência conhecidos: Atom, um conjunto de padrões de troca e atualização de dados como XML e JSON JavaScript Object Notation (), um formato de troca de dados com base em texto usado extensivamente em aplicativos AJAX.</span><span class="sxs-lookup"><span data-stu-id="ecd09-109">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>

<span data-ttu-id="ecd09-110">WCF Data Services pode expor dados provenientes de várias fontes como feeds OData.</span><span class="sxs-lookup"><span data-stu-id="ecd09-110">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="ecd09-111">Ferramentas do Visual Studio facilitam a criação de um serviço baseado em OData usando um modelo de dados do ADO.NET Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ecd09-111">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="ecd09-112">Você também pode criar feeds OData com base em classes do common language runtime (CLR) e dados de até mesmo associação tardia ou não tipados.</span><span class="sxs-lookup"><span data-stu-id="ecd09-112">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="ecd09-113">WCF Data Services também inclui um conjunto de bibliotecas de cliente, um para aplicativos de cliente do .NET Framework gerais e outro especificamente para aplicativos baseados no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ecd09-113">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="ecd09-114">Essas bibliotecas de cliente fornecem um modelo de programação baseado em objeto quando você acessa um feed OData em ambientes como o .NET Framework e Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ecd09-114">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="ecd09-115">Onde devo começar?</span><span class="sxs-lookup"><span data-stu-id="ecd09-115">Where Should I Start?</span></span>

<span data-ttu-id="ecd09-116">Dependendo dos seus interesses, considere a introdução ao WCF Data Services em um dos tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ecd09-116">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="ecd09-117">Desejo ir diretamente para...</span><span class="sxs-lookup"><span data-stu-id="ecd09-117">I want to jump right in...</span></span>

- <span data-ttu-id="ecd09-118">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="ecd09-118">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>

- [<span data-ttu-id="ecd09-119">Introdução</span><span class="sxs-lookup"><span data-stu-id="ecd09-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

- <span data-ttu-id="ecd09-120">[Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)</span><span class="sxs-lookup"><span data-stu-id="ecd09-120">[Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782)</span></span>

- <span data-ttu-id="ecd09-121">[Silverlight Quickstart for Windows Phone Development](https://go.microsoft.com/fwlink/?LinkID=214535) (Guia de início rápido do Silverlight para desenvolvimento do Windows Phone)</span><span class="sxs-lookup"><span data-stu-id="ecd09-121">[Silverlight Quickstart for Windows Phone Development](https://go.microsoft.com/fwlink/?LinkID=214535)</span></span>

<span data-ttu-id="ecd09-122">Mostre-me apenas algum código...</span><span class="sxs-lookup"><span data-stu-id="ecd09-122">Just show me some code...</span></span>

- <span data-ttu-id="ecd09-123">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) (Início rápido)</span><span class="sxs-lookup"><span data-stu-id="ecd09-123">[Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)</span></span>

- [<span data-ttu-id="ecd09-124">Como: Executar consultas de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="ecd09-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="ecd09-125">Como: Associar dados aos elementos do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ecd09-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="ecd09-126">Quero saber mais sobre OData...</span><span class="sxs-lookup"><span data-stu-id="ecd09-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="ecd09-127">White paper: Introdução ao OData</span><span class="sxs-lookup"><span data-stu-id="ecd09-127">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- [<span data-ttu-id="ecd09-128">Site do Protocolo Open Data</span><span class="sxs-lookup"><span data-stu-id="ecd09-128">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

- [<span data-ttu-id="ecd09-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="ecd09-129">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

- [<span data-ttu-id="ecd09-130">OData: Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="ecd09-130">OData: Frequently Asked Questions</span></span>](https://go.microsoft.com/fwlink/?LinkId=185867)

<span data-ttu-id="ecd09-131">Eu desejo assistir a alguns vídeos...</span><span class="sxs-lookup"><span data-stu-id="ecd09-131">I want to watch some videos...</span></span>

- <span data-ttu-id="ecd09-132">[Beginner's Guide to WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864) (Guia do iniciante do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecd09-132">[Beginner's Guide to WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=220864)</span></span>

- <span data-ttu-id="ecd09-133">[WCF Data Services Developer Videos](https://go.microsoft.com/fwlink/?LinkId=220861) (Vídeos para desenvolvedores do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecd09-133">[WCF Data Services Developer Videos](https://go.microsoft.com/fwlink/?LinkId=220861)</span></span>

- [<span data-ttu-id="ecd09-134">OData: Site de desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="ecd09-134">OData: Developers Web site</span></span>](https://go.microsoft.com/fwlink/?LinkId=185866)

<span data-ttu-id="ecd09-135">Desejo ver exemplos de ponta a ponta...</span><span class="sxs-lookup"><span data-stu-id="ecd09-135">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="ecd09-136">[WCF Data Services Documentation Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkID=220865) (Amostras de documentação do WCF Data Services na galeria de amostras do MSDN)</span><span class="sxs-lookup"><span data-stu-id="ecd09-136">[WCF Data Services Documentation Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkID=220865)</span></span>

- <span data-ttu-id="ecd09-137">[Other WCF Data Services Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkId=220866) (Outras amostras do WCF Data Services na galeria de amostras do MSDN)</span><span class="sxs-lookup"><span data-stu-id="ecd09-137">[Other WCF Data Services Samples on MSDN Samples Gallery](https://go.microsoft.com/fwlink/?LinkId=220866)</span></span>

- [<span data-ttu-id="ecd09-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="ecd09-138">OData: SDK</span></span>](https://go.microsoft.com/fwlink/?LinkID=185248)

<span data-ttu-id="ecd09-139">Como ele se integra ao Visual Studio?</span><span class="sxs-lookup"><span data-stu-id="ecd09-139">How does it integrate with Visual Studio?</span></span>

- <span data-ttu-id="ecd09-140">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="ecd09-140">[Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)</span></span>

- <span data-ttu-id="ecd09-141">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md) (Criando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="ecd09-141">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md)</span></span>

- <span data-ttu-id="ecd09-142">[Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md) (Provedor de Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="ecd09-142">[Entity Framework Provider](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)</span></span>

<span data-ttu-id="ecd09-143">O que posso fazer com ele?</span><span class="sxs-lookup"><span data-stu-id="ecd09-143">What can I do with it?</span></span>

- [<span data-ttu-id="ecd09-144">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ecd09-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

- [<span data-ttu-id="ecd09-145">White paper: Introdução ao OData</span><span class="sxs-lookup"><span data-stu-id="ecd09-145">Whitepaper: Introducing OData</span></span>](https://go.microsoft.com/fwlink/?LinkId=220867)

- <span data-ttu-id="ecd09-146">[Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md) (Cenários de aplicativo)</span><span class="sxs-lookup"><span data-stu-id="ecd09-146">[Application Scenarios](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)</span></span>

<span data-ttu-id="ecd09-147">Desejo usar o Silverlight...</span><span class="sxs-lookup"><span data-stu-id="ecd09-147">I want to use Silverlight...</span></span>

- <span data-ttu-id="ecd09-148">[Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782) (Início rápido do Silverlight)</span><span class="sxs-lookup"><span data-stu-id="ecd09-148">[Silverlight Quickstart](https://go.microsoft.com/fwlink/?LinkID=192782)</span></span>

- [<span data-ttu-id="ecd09-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="ecd09-149">WCF Data Services (Silverlight)</span></span>](https://go.microsoft.com/fwlink/?LinkID=143149)

- <span data-ttu-id="ecd09-150">[Getting Started with Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366) (Introdução ao Silverlight)</span><span class="sxs-lookup"><span data-stu-id="ecd09-150">[Getting Started with Silverlight](https://go.microsoft.com/fwlink/?LinkId=148366)</span></span>

<span data-ttu-id="ecd09-151">Desejo usar LINQ...</span><span class="sxs-lookup"><span data-stu-id="ecd09-151">I want to use LINQ...</span></span>

- <span data-ttu-id="ecd09-152">[Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="ecd09-152">[Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)</span></span>

- <span data-ttu-id="ecd09-153">[LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)</span><span class="sxs-lookup"><span data-stu-id="ecd09-153">[LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)</span></span>

- [<span data-ttu-id="ecd09-154">Como: Executar consultas de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="ecd09-154">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="ecd09-155">Eu ainda preciso de mais algumas informações...</span><span class="sxs-lookup"><span data-stu-id="ecd09-155">I still need some more information...</span></span>

- [<span data-ttu-id="ecd09-156">Blog da equipe do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="ecd09-156">WCF Data Services Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=150511)

- [<span data-ttu-id="ecd09-157">Recursos</span><span class="sxs-lookup"><span data-stu-id="ecd09-157">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

- <span data-ttu-id="ecd09-158">[WCF Data Services Developer Center](https://go.microsoft.com/fwlink/?LinkId=220868) (Central de desenvolvedores do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecd09-158">[WCF Data Services Developer Center](https://go.microsoft.com/fwlink/?LinkId=220868)</span></span>

- [<span data-ttu-id="ecd09-159">Site do Protocolo Open Data</span><span class="sxs-lookup"><span data-stu-id="ecd09-159">Open Data Protocol Web site</span></span>](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a><span data-ttu-id="ecd09-160">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ecd09-160">In This Section</span></span>

[<span data-ttu-id="ecd09-161">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ecd09-161">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

<span data-ttu-id="ecd09-162">Fornece uma visão geral dos recursos e funcionalidades disponíveis no WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="ecd09-162">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="ecd09-163">[O que há de novo no WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="ecd09-163">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="ecd09-164">Descreve a nova funcionalidade no WCF Data Services e o suporte para novos recursos do OData.</span><span class="sxs-lookup"><span data-stu-id="ecd09-164">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="ecd09-165">Introdução</span><span class="sxs-lookup"><span data-stu-id="ecd09-165">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

<span data-ttu-id="ecd09-166">Descreve como expor e consumir feeds de OData usando o WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="ecd09-166">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

<span data-ttu-id="ecd09-167">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecd09-167">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)</span></span>

<span data-ttu-id="ecd09-168">Descreve como criar e configurar um serviço de dados que expõe feeds OData.</span><span class="sxs-lookup"><span data-stu-id="ecd09-168">Describes how to create and configure a data service that exposes OData feeds.</span></span>

<span data-ttu-id="ecd09-169">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ecd09-169">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)</span></span>

<span data-ttu-id="ecd09-170">Descreve como usar bibliotecas de cliente para consumir feeds de OData de um aplicativo de cliente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecd09-170">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecd09-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecd09-171">See also</span></span>

- <span data-ttu-id="ecd09-172">[Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919) [REST (Transferência de Estado Representacional)]</span><span class="sxs-lookup"><span data-stu-id="ecd09-172">[Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)</span></span>
