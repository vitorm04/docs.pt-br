---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: Um guia que fornece diretrizes de ponta a ponta para a criação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449316"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="1b94f-103">Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure</span><span class="sxs-lookup"><span data-stu-id="1b94f-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Livro de folhas de rosto do guia de aplicativos Web do arquiteto moderno.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="1b94f-105">**Edição v 3.1** -atualizado para ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1b94f-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="1b94f-106">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="1b94f-106">PUBLISHED BY</span></span>

<span data-ttu-id="1b94f-107">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b94f-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="1b94f-108">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1b94f-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="1b94f-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="1b94f-109">One Microsoft Way</span></span>

<span data-ttu-id="1b94f-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="1b94f-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="1b94f-111">Copyright © 2020 da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1b94f-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="1b94f-112">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="1b94f-112">All rights reserved.</span></span> <span data-ttu-id="1b94f-113">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="1b94f-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="1b94f-114">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="1b94f-114">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="1b94f-115">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="1b94f-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="1b94f-116">Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="1b94f-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="1b94f-117">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="1b94f-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="1b94f-118">A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b94f-118">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="1b94f-119">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="1b94f-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="1b94f-120">O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.</span><span class="sxs-lookup"><span data-stu-id="1b94f-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="1b94f-121">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="1b94f-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="1b94f-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="1b94f-122">Author:</span></span>

> <span data-ttu-id="1b94f-123">**Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="1b94f-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="1b94f-124">Editores:</span><span class="sxs-lookup"><span data-stu-id="1b94f-124">Editors:</span></span>

> <span data-ttu-id="1b94f-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="1b94f-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="1b94f-126">Introdução</span><span class="sxs-lookup"><span data-stu-id="1b94f-126">Introduction</span></span>

<span data-ttu-id="1b94f-127">O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET.</span><span class="sxs-lookup"><span data-stu-id="1b94f-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="1b94f-128">Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1b94f-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="1b94f-129">Suporte para plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="1b94f-129">Cross-platform support.</span></span>

- <span data-ttu-id="1b94f-130">Uso de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="1b94f-130">Use of microservices.</span></span>

- <span data-ttu-id="1b94f-131">Uso de contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="1b94f-131">Use of Docker containers.</span></span>

- <span data-ttu-id="1b94f-132">Requisitos de alto desempenho e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="1b94f-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="1b94f-133">Controle de versão lado a lado para versões do .NET por aplicativo no mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="1b94f-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="1b94f-134">Aplicativos .NET tradicionais poderão dar suporte a vários desses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.</span><span class="sxs-lookup"><span data-stu-id="1b94f-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="1b94f-135">Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="1b94f-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="1b94f-136">Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:</span><span class="sxs-lookup"><span data-stu-id="1b94f-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="1b94f-137">Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, gerenciamento de servidor, etc.)</span><span class="sxs-lookup"><span data-stu-id="1b94f-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="1b94f-138">Preços flexíveis (pague com base no uso, não pela capacidade ociosa).</span><span class="sxs-lookup"><span data-stu-id="1b94f-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="1b94f-139">Confiabilidade extrema.</span><span class="sxs-lookup"><span data-stu-id="1b94f-139">Extreme reliability.</span></span>

- <span data-ttu-id="1b94f-140">Melhoria na mobilidade de aplicativo: altere facilmente onde e como seu aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="1b94f-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="1b94f-141">Capacidade flexível: aumente ou reduza com base em necessidades reais.</span><span class="sxs-lookup"><span data-stu-id="1b94f-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="1b94f-142">A criação de aplicativos Web com o ASP.NET Core, hospedados no Azure, oferece várias vantagens competitivas em relação às alternativas tradicionais.</span><span class="sxs-lookup"><span data-stu-id="1b94f-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="1b94f-143">O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos.</span><span class="sxs-lookup"><span data-stu-id="1b94f-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="1b94f-144">Neste guia, você aprenderá como arquitetar seus aplicativos ASP.NET Core para aproveitar melhor essas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="1b94f-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="1b94f-145">Finalidade</span><span class="sxs-lookup"><span data-stu-id="1b94f-145">Purpose</span></span>

<span data-ttu-id="1b94f-146">Este guia fornece diretrizes ponta a ponta para a compilação de aplicativos Web *monolíticos* usando o ASP.NET Core e o Azure.</span><span class="sxs-lookup"><span data-stu-id="1b94f-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="1b94f-147">Nesse contexto, "monolítico" refere-se ao fato de que esses aplicativos são implantados como uma única unidade, não como uma coleção de serviços e aplicativos em interação.</span><span class="sxs-lookup"><span data-stu-id="1b94f-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="1b94f-148">Este guia é complementar aos ["_microserviços .net. Arquitetura para aplicativos .NET em contêineres_"](../microservices/index.md) que se concentram mais no Docker, em microservices e na implantação de contêineres para hospedar aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="1b94f-148">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="1b94f-149">Microsserviços do .NET.</span><span class="sxs-lookup"><span data-stu-id="1b94f-149">.NET Microservices.</span></span> <span data-ttu-id="1b94f-150">Arquitetura de aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="1b94f-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="1b94f-151">**livro eletrônico**</span><span class="sxs-lookup"><span data-stu-id="1b94f-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="1b94f-152">**Aplicativo de exemplo**</span><span class="sxs-lookup"><span data-stu-id="1b94f-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="1b94f-153">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="1b94f-153">Who should use this guide</span></span>

<span data-ttu-id="1b94f-154">O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.</span><span class="sxs-lookup"><span data-stu-id="1b94f-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="1b94f-155">Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET ou com o Azure e estão buscando informações para saber se é interessante atualizar seus projetos novos ou existentes para o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1b94f-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="1b94f-156">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="1b94f-156">How you can use this guide</span></span>

<span data-ttu-id="1b94f-157">Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="1b94f-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="1b94f-158">Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas.</span><span class="sxs-lookup"><span data-stu-id="1b94f-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="1b94f-159">O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência.</span><span class="sxs-lookup"><span data-stu-id="1b94f-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="1b94f-160">Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b94f-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="1b94f-161">Confira os princípios do guia, a cobertura das opções de arquitetura e de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b94f-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="1b94f-162">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="1b94f-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="1b94f-163">Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="1b94f-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="1b94f-164">Referências</span><span class="sxs-lookup"><span data-stu-id="1b94f-164">References</span></span>

- <span data-ttu-id="1b94f-165">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="1b94f-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="1b94f-166">Próximo</span><span class="sxs-lookup"><span data-stu-id="1b94f-166">Next</span></span>](modern-web-applications-characteristics.md)
