---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: "Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Introdução"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db9f0ddd875df1f84bcc5681ee1383b0185f8b7e
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="f0fcd-103">Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure</span><span class="sxs-lookup"><span data-stu-id="f0fcd-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![imagem da capa](./media/cover.jpg)


<span data-ttu-id="f0fcd-105">O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-105">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="f0fcd-106">Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f0fcd-106">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="f0fcd-107">Suporte de multiplaforma</span><span class="sxs-lookup"><span data-stu-id="f0fcd-107">Cross-platform support</span></span>

-   <span data-ttu-id="f0fcd-108">Uso de microsserviços</span><span class="sxs-lookup"><span data-stu-id="f0fcd-108">Use of microservices</span></span>

-   <span data-ttu-id="f0fcd-109">Uso de contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="f0fcd-109">Use of Docker containers</span></span>

-   <span data-ttu-id="f0fcd-110">Requisitos de alto desempenho e escalabilidade</span><span class="sxs-lookup"><span data-stu-id="f0fcd-110">High performance and scalability requirements</span></span>

-   <span data-ttu-id="f0fcd-111">Controle de versão lado a lado de versões do .NET pelo aplicativo no mesmo servidor</span><span class="sxs-lookup"><span data-stu-id="f0fcd-111">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="f0fcd-112">Aplicativos .NET tradicionais poderão dar suporte a esses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-112">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="f0fcd-113">Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-113">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="f0fcd-114">Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:</span><span class="sxs-lookup"><span data-stu-id="f0fcd-114">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="f0fcd-115">Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, etc.)</span><span class="sxs-lookup"><span data-stu-id="f0fcd-115">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="f0fcd-116">Preços flexíveis (pague com base no uso, não na capacidade ociosa)</span><span class="sxs-lookup"><span data-stu-id="f0fcd-116">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="f0fcd-117">Confiabilidade extrema</span><span class="sxs-lookup"><span data-stu-id="f0fcd-117">Extreme reliability</span></span>

-   <span data-ttu-id="f0fcd-118">Melhoria na mobilidade de aplicativo; altere facilmente onde e como seu aplicativo é implantado</span><span class="sxs-lookup"><span data-stu-id="f0fcd-118">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="f0fcd-119">Capacidade flexível; expandir ou reduzir com base em necessidades reais</span><span class="sxs-lookup"><span data-stu-id="f0fcd-119">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="f0fcd-120">Compilar aplicativos Web com o ASP.NET Core, hospedado no Microsoft Azure, oferece várias vantagens competitivas sobre as alternativas tradicionais.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-120">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="f0fcd-121">O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-121">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="f0fcd-122">Neste guia, você aprenderá como arquitetar seus aplicativos do ASP.NET Core para aproveitar melhor essas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-122">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="f0fcd-123">Finalidade</span><span class="sxs-lookup"><span data-stu-id="f0fcd-123">Purpose</span></span>

<span data-ttu-id="f0fcd-124">Este guia fornece diretrizes ponta a ponta para a compilação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-124">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="f0fcd-125">Este guia é um complemento para o “*Architecting and Developing Containerized and Microservice-based Applications with .NET*” (Arquitetura e desenvolvimento de aplicativos em contêineres e com microsserviços) que se concentra mais no Docker, Microsserviços e Implantação de Contêineres para hospedar aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-125">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="f0fcd-126">Arquitetura e desenvolvimento de aplicativos baseados em microsserviços em contêineres no .NET</span><span class="sxs-lookup"><span data-stu-id="f0fcd-126">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="f0fcd-127">**livro eletrônico**</span><span class="sxs-lookup"><span data-stu-id="f0fcd-127">**e-book**</span></span>  
> <span data-ttu-id="f0fcd-128"><http://aka.ms/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="f0fcd-128"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="f0fcd-129">**Aplicativo de exemplo**</span><span class="sxs-lookup"><span data-stu-id="f0fcd-129">**Sample Application**</span></span>  
> <span data-ttu-id="f0fcd-130"><http://aka.ms/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="f0fcd-130"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="f0fcd-131">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="f0fcd-131">Who should use this guide</span></span>

<span data-ttu-id="f0fcd-132">O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-132">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="f0fcd-133">Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET e/ou o Azure e estão procurando informações sobre se faz sentido para atualizar para o ASP.NET Core para projetos novos ou existentes.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-133">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="f0fcd-134">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="f0fcd-134">How you can use this guide</span></span>

<span data-ttu-id="f0fcd-135">Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-135">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="f0fcd-136">Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-136">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="f0fcd-137">O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-137">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="f0fcd-138">Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-138">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="f0fcd-139">Consulte os princípios do guia, a cobertura da arquitetura, as opções de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-139">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="f0fcd-140">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-140">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="f0fcd-141">Ter todas as pessoas trabalhando em um conjunto comum de terminologia e princípios subjacentes ajudará a garantir a aplicação consistente dos padrões e práticas arquitetônicos.</span><span class="sxs-lookup"><span data-stu-id="f0fcd-141">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="f0fcd-142">Referências</span><span class="sxs-lookup"><span data-stu-id="f0fcd-142">References</span></span>
- <span data-ttu-id="f0fcd-143">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="f0fcd-143">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="f0fcd-144"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="f0fcd-144"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f0fcd-145">[Next] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="f0fcd-145">[Next] (modern-web-applications-characteristics.md)</span></span>
