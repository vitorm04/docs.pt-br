---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: Um guia que fornece diretrizes de ponta a ponta para a criação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 936a068507116033ad178f26e77945f30f70387e
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507187"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="6f41b-103">Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure</span><span class="sxs-lookup"><span data-stu-id="6f41b-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Livro de folhas de rosto do guia de aplicativos Web do arquiteto moderno.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="6f41b-105">**Edição v 3.1** -atualizado para ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6f41b-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="6f41b-106">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="6f41b-106">PUBLISHED BY</span></span>

<span data-ttu-id="6f41b-107">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f41b-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="6f41b-108">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="6f41b-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="6f41b-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="6f41b-109">One Microsoft Way</span></span>

<span data-ttu-id="6f41b-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="6f41b-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="6f41b-111">Copyright © 2020 da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="6f41b-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="6f41b-112">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="6f41b-112">All rights reserved.</span></span> <span data-ttu-id="6f41b-113">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="6f41b-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="6f41b-114">Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="6f41b-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="6f41b-115">Os pontos de vista, as opiniões e as informações expressos neste livro, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="6f41b-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="6f41b-116"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="6f41b-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="6f41b-117">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="6f41b-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="6f41b-118">A Microsoft e as marcas listadas em https://www.microsoft.com na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6f41b-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="6f41b-119">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="6f41b-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="6f41b-120">O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.</span><span class="sxs-lookup"><span data-stu-id="6f41b-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="6f41b-121">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="6f41b-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="6f41b-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="6f41b-122">Author:</span></span>

> <span data-ttu-id="6f41b-123">**Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="6f41b-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="6f41b-124">Editores:</span><span class="sxs-lookup"><span data-stu-id="6f41b-124">Editors:</span></span>

> <span data-ttu-id="6f41b-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="6f41b-125">**Maira Wenzel**</span></span>

## <a name="action-links"></a><span data-ttu-id="6f41b-126">Links de ação</span><span class="sxs-lookup"><span data-stu-id="6f41b-126">Action links</span></span>

- <span data-ttu-id="6f41b-127">Este livro eletrônico também está disponível em um formato PDF (somente versão em inglês) [Download](https://aka.ms/webappebook)</span><span class="sxs-lookup"><span data-stu-id="6f41b-127">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/webappebook)</span></span>

- <span data-ttu-id="6f41b-128">Clonar/bifurcar o aplicativo de referência [eShopOnWeb no GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span><span class="sxs-lookup"><span data-stu-id="6f41b-128">Clone/Fork the reference application [eShopOnWeb on GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span></span>

## <a name="introduction"></a><span data-ttu-id="6f41b-129">Introdução</span><span class="sxs-lookup"><span data-stu-id="6f41b-129">Introduction</span></span>

<span data-ttu-id="6f41b-130">O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET.</span><span class="sxs-lookup"><span data-stu-id="6f41b-130">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="6f41b-131">Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="6f41b-131">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="6f41b-132">Suporte para plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="6f41b-132">Cross-platform support.</span></span>

- <span data-ttu-id="6f41b-133">Uso de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="6f41b-133">Use of microservices.</span></span>

- <span data-ttu-id="6f41b-134">Uso de contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="6f41b-134">Use of Docker containers.</span></span>

- <span data-ttu-id="6f41b-135">Requisitos de alto desempenho e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="6f41b-135">High performance and scalability requirements.</span></span>

- <span data-ttu-id="6f41b-136">Controle de versão lado a lado para versões do .NET por aplicativo no mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="6f41b-136">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="6f41b-137">Aplicativos .NET tradicionais poderão dar suporte a vários desses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.</span><span class="sxs-lookup"><span data-stu-id="6f41b-137">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="6f41b-138">Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="6f41b-138">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="6f41b-139">Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:</span><span class="sxs-lookup"><span data-stu-id="6f41b-139">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="6f41b-140">Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, gerenciamento de servidor, etc.)</span><span class="sxs-lookup"><span data-stu-id="6f41b-140">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="6f41b-141">Preços flexíveis (pague com base no uso, não pela capacidade ociosa).</span><span class="sxs-lookup"><span data-stu-id="6f41b-141">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="6f41b-142">Confiabilidade extrema.</span><span class="sxs-lookup"><span data-stu-id="6f41b-142">Extreme reliability.</span></span>

- <span data-ttu-id="6f41b-143">Melhoria na mobilidade de aplicativo: altere facilmente onde e como seu aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="6f41b-143">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="6f41b-144">Capacidade flexível: aumente ou reduza com base em necessidades reais.</span><span class="sxs-lookup"><span data-stu-id="6f41b-144">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="6f41b-145">A criação de aplicativos Web com o ASP.NET Core, hospedados no Azure, oferece várias vantagens competitivas em relação às alternativas tradicionais.</span><span class="sxs-lookup"><span data-stu-id="6f41b-145">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="6f41b-146">O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos.</span><span class="sxs-lookup"><span data-stu-id="6f41b-146">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="6f41b-147">Neste guia, você aprenderá como arquitetar seus aplicativos ASP.NET Core para aproveitar melhor essas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="6f41b-147">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="6f41b-148">Finalidade</span><span class="sxs-lookup"><span data-stu-id="6f41b-148">Purpose</span></span>

<span data-ttu-id="6f41b-149">Este guia fornece orientação de ponta a ponta sobre a criação de aplicativos Web *monolíticos* usando o ASP.NET Core e o Azure.</span><span class="sxs-lookup"><span data-stu-id="6f41b-149">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="6f41b-150">Nesse contexto, "monolítico" refere-se ao fato de que esses aplicativos são implantados como uma única unidade, não como uma coleção de serviços e aplicativos em interação.</span><span class="sxs-lookup"><span data-stu-id="6f41b-150">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="6f41b-151">Este guia é complementar aos ["_microserviços .net. Arquitetura para aplicativos .NET em contêineres_"](../microservices/index.md), que se concentram mais no Docker, em microservices e na implantação de contêineres para hospedar aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="6f41b-151">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="6f41b-152">Microsserviços do .NET.</span><span class="sxs-lookup"><span data-stu-id="6f41b-152">.NET Microservices.</span></span> <span data-ttu-id="6f41b-153">Arquitetura de aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="6f41b-153">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="6f41b-154">**livro eletrônico**</span><span class="sxs-lookup"><span data-stu-id="6f41b-154">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="6f41b-155">**Aplicativo de exemplo**</span><span class="sxs-lookup"><span data-stu-id="6f41b-155">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="6f41b-156">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="6f41b-156">Who should use this guide</span></span>

<span data-ttu-id="6f41b-157">O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.</span><span class="sxs-lookup"><span data-stu-id="6f41b-157">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="6f41b-158">Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET ou com o Azure e estão buscando informações para saber se é interessante atualizar seus projetos novos ou existentes para o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f41b-158">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="6f41b-159">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="6f41b-159">How you can use this guide</span></span>

<span data-ttu-id="6f41b-160">Este guia foi condensado em um documento relativamente pequeno que se concentra na criação de aplicativos Web com as tecnologias modernas do .NET e o Azure.</span><span class="sxs-lookup"><span data-stu-id="6f41b-160">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="6f41b-161">Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas.</span><span class="sxs-lookup"><span data-stu-id="6f41b-161">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="6f41b-162">O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência.</span><span class="sxs-lookup"><span data-stu-id="6f41b-162">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="6f41b-163">Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f41b-163">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="6f41b-164">Confira os princípios do guia, a cobertura das opções de arquitetura e de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f41b-164">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="6f41b-165">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="6f41b-165">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="6f41b-166">Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="6f41b-166">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="6f41b-167">Referências</span><span class="sxs-lookup"><span data-stu-id="6f41b-167">References</span></span>

- <span data-ttu-id="6f41b-168">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="6f41b-168">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="6f41b-169">Avançar</span><span class="sxs-lookup"><span data-stu-id="6f41b-169">Next</span></span>](modern-web-applications-characteristics.md)
