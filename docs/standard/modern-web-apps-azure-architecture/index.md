---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: "Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Introdução"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="3ba33-103">Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure</span><span class="sxs-lookup"><span data-stu-id="3ba33-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

<span data-ttu-id="3ba33-104">O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET.</span><span class="sxs-lookup"><span data-stu-id="3ba33-104">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="3ba33-105">Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="3ba33-105">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="3ba33-106">Suporte de multiplaforma</span><span class="sxs-lookup"><span data-stu-id="3ba33-106">Cross-platform support</span></span>

-   <span data-ttu-id="3ba33-107">Uso de microsserviços</span><span class="sxs-lookup"><span data-stu-id="3ba33-107">Use of microservices</span></span>

-   <span data-ttu-id="3ba33-108">Uso de contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="3ba33-108">Use of Docker containers</span></span>

-   <span data-ttu-id="3ba33-109">Requisitos de alto desempenho e escalabilidade</span><span class="sxs-lookup"><span data-stu-id="3ba33-109">High performance and scalability requirements</span></span>

-   <span data-ttu-id="3ba33-110">Controle de versão lado a lado de versões do .NET pelo aplicativo no mesmo servidor</span><span class="sxs-lookup"><span data-stu-id="3ba33-110">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="3ba33-111">Aplicativos .NET tradicionais poderão dar suporte a esses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.</span><span class="sxs-lookup"><span data-stu-id="3ba33-111">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="3ba33-112">Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3ba33-112">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="3ba33-113">Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:</span><span class="sxs-lookup"><span data-stu-id="3ba33-113">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="3ba33-114">Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, etc.)</span><span class="sxs-lookup"><span data-stu-id="3ba33-114">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="3ba33-115">Preços flexíveis (pague com base no uso, não na capacidade ociosa)</span><span class="sxs-lookup"><span data-stu-id="3ba33-115">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="3ba33-116">Confiabilidade extrema</span><span class="sxs-lookup"><span data-stu-id="3ba33-116">Extreme reliability</span></span>

-   <span data-ttu-id="3ba33-117">Melhoria na mobilidade de aplicativo; altere facilmente onde e como seu aplicativo é implantado</span><span class="sxs-lookup"><span data-stu-id="3ba33-117">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="3ba33-118">Capacidade flexível; expandir ou reduzir com base em necessidades reais</span><span class="sxs-lookup"><span data-stu-id="3ba33-118">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="3ba33-119">Compilar aplicativos Web com o ASP.NET Core, hospedado no Microsoft Azure, oferece várias vantagens competitivas sobre as alternativas tradicionais.</span><span class="sxs-lookup"><span data-stu-id="3ba33-119">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="3ba33-120">O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos.</span><span class="sxs-lookup"><span data-stu-id="3ba33-120">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="3ba33-121">Neste guia, você aprenderá como arquitetar seus aplicativos do ASP.NET Core para aproveitar melhor essas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="3ba33-121">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="3ba33-122">Finalidade</span><span class="sxs-lookup"><span data-stu-id="3ba33-122">Purpose</span></span>

<span data-ttu-id="3ba33-123">Este guia fornece diretrizes ponta a ponta para a compilação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.</span><span class="sxs-lookup"><span data-stu-id="3ba33-123">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="3ba33-124">Este guia é um complemento para o “*Architecting and Developing Containerized and Microservice-based Applications with .NET*” (Arquitetura e desenvolvimento de aplicativos em contêineres e com microsserviços) que se concentra mais no Docker, Microsserviços e Implantação de Contêineres para hospedar aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="3ba33-124">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="3ba33-125">Arquitetura e desenvolvimento de aplicativos baseados em microsserviços em contêineres no .NET</span><span class="sxs-lookup"><span data-stu-id="3ba33-125">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="3ba33-126">**livro eletrônico**</span><span class="sxs-lookup"><span data-stu-id="3ba33-126">**e-book**</span></span>  
> <span data-ttu-id="3ba33-127"><http://aka.ms/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="3ba33-127"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="3ba33-128">**Aplicativo de exemplo**</span><span class="sxs-lookup"><span data-stu-id="3ba33-128">**Sample Application**</span></span>  
> <span data-ttu-id="3ba33-129"><http://aka.ms/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="3ba33-129"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="3ba33-130">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="3ba33-130">Who should use this guide</span></span>

<span data-ttu-id="3ba33-131">O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.</span><span class="sxs-lookup"><span data-stu-id="3ba33-131">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="3ba33-132">Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET e/ou o Azure e estão procurando informações sobre se faz sentido para atualizar para o ASP.NET Core para projetos novos ou existentes.</span><span class="sxs-lookup"><span data-stu-id="3ba33-132">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="3ba33-133">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="3ba33-133">How you can use this guide</span></span>

<span data-ttu-id="3ba33-134">Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3ba33-134">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="3ba33-135">Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas.</span><span class="sxs-lookup"><span data-stu-id="3ba33-135">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="3ba33-136">O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência.</span><span class="sxs-lookup"><span data-stu-id="3ba33-136">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="3ba33-137">Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ba33-137">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="3ba33-138">Consulte os princípios do guia, a cobertura da arquitetura, as opções de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ba33-138">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="3ba33-139">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="3ba33-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="3ba33-140">Ter todas as pessoas trabalhando em um conjunto comum de terminologia e princípios subjacentes ajudará a garantir a aplicação consistente dos padrões e práticas arquitetônicos.</span><span class="sxs-lookup"><span data-stu-id="3ba33-140">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="3ba33-141">Referências</span><span class="sxs-lookup"><span data-stu-id="3ba33-141">References</span></span>
- <span data-ttu-id="3ba33-142">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="3ba33-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="3ba33-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="3ba33-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3ba33-144">[Next] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="3ba33-144">[Next] (modern-web-applications-characteristics.md)</span></span>
