---
title: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure
description: Um guia que fornece diretrizes de ponta a ponta para a criação de aplicativos Web monolíticos usando o ASP.NET Core e o Azure.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 5e85126cbec23bdebd510b103478b3c362ef71fa
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827858"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="e4bc6-103">Arquitetar Aplicativos Web Modernos com o ASP.NET Core e o Azure</span><span class="sxs-lookup"><span data-stu-id="e4bc6-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![imagem da capa](./media/cover.png)

<span data-ttu-id="e4bc6-105">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="e4bc6-105">PUBLISHED BY</span></span>

<span data-ttu-id="e4bc6-106">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e4bc6-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e4bc6-107">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4bc6-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e4bc6-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e4bc6-108">One Microsoft Way</span></span>

<span data-ttu-id="e4bc6-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e4bc6-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e4bc6-110">Copyright © 2019, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e4bc6-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="e4bc6-111">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-111">All rights reserved.</span></span> <span data-ttu-id="e4bc6-112">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e4bc6-113">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="e4bc6-114">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e4bc6-115">Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e4bc6-116">Nenhuma associação ou conexão real é intencional ou deve ser deduzida.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e4bc6-117">A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e4bc6-118">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e4bc6-119">O logotipo de baleia do Docker é uma marca registrada da Docker, Inc. usado mediante permissão.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e4bc6-120">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="e4bc6-121">Autor:</span><span class="sxs-lookup"><span data-stu-id="e4bc6-121">Author:</span></span>

> <span data-ttu-id="e4bc6-122">**Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="e4bc6-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="e4bc6-123">Editores:</span><span class="sxs-lookup"><span data-stu-id="e4bc6-123">Editors:</span></span>

> <span data-ttu-id="e4bc6-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="e4bc6-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="e4bc6-125">Introdução</span><span class="sxs-lookup"><span data-stu-id="e4bc6-125">Introduction</span></span>

<span data-ttu-id="e4bc6-126">O .NET Core e o ASP.NET Core oferecem várias vantagens sobre o desenvolvimento tradicional no .NET.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="e4bc6-127">Você deve usar o .NET Core para seus aplicativos de servidor se alguns ou todos os itens a seguir forem importantes para o sucesso do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e4bc6-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="e4bc6-128">Suporte para plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-128">Cross-platform support.</span></span>

- <span data-ttu-id="e4bc6-129">Uso de microsserviços.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-129">Use of microservices.</span></span>

- <span data-ttu-id="e4bc6-130">Uso de contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-130">Use of Docker containers.</span></span>

- <span data-ttu-id="e4bc6-131">Requisitos de alto desempenho e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="e4bc6-132">Controle de versão lado a lado para versões do .NET por aplicativo no mesmo servidor.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="e4bc6-133">Aplicativos .NET tradicionais poderão dar suporte a vários desses requisitos, porém o ASP.NET Core e .NET Core foram otimizados para proporcionar suporte aprimorado para os cenários acima.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-133">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="e4bc6-134">Cada vez mais empresas estão optando por hospedar seus aplicativos Web na nuvem usando serviços como o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="e4bc6-135">Considere hospedar seu aplicativo na nuvem se os seguintes itens forem importantes para seu aplicativo ou organização:</span><span class="sxs-lookup"><span data-stu-id="e4bc6-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="e4bc6-136">Investimento reduzido nos custos de data center (hardware, software, espaço, utilitários, gerenciamento de servidor, etc.)</span><span class="sxs-lookup"><span data-stu-id="e4bc6-136">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="e4bc6-137">Preços flexíveis (pague com base no uso, não pela capacidade ociosa).</span><span class="sxs-lookup"><span data-stu-id="e4bc6-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="e4bc6-138">Confiabilidade extrema.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-138">Extreme reliability.</span></span>

- <span data-ttu-id="e4bc6-139">Melhoria na mobilidade de aplicativo: altere facilmente onde e como seu aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="e4bc6-140">Capacidade flexível: aumente ou reduza com base em necessidades reais.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="e4bc6-141">A criação de aplicativos Web com o ASP.NET Core, hospedados no Azure, oferece várias vantagens competitivas em relação às alternativas tradicionais.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="e4bc6-142">O ASP.NET Core é otimizado para práticas de desenvolvimento de aplicativos Web e cenários de hospedagem em nuvem modernos.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="e4bc6-143">Neste guia, você aprenderá como arquitetar seus aplicativos ASP.NET Core para aproveitar melhor essas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="e4bc6-144">Finalidade</span><span class="sxs-lookup"><span data-stu-id="e4bc6-144">Purpose</span></span>

<span data-ttu-id="e4bc6-145">Este guia fornece diretrizes ponta a ponta para a compilação de aplicativos Web *monolíticos* usando o ASP.NET Core e o Azure.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-145">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="e4bc6-146">Nesse contexto, "monolítico" refere-se ao fato de que esses aplicativos são implantados como uma única unidade, não como uma coleção de serviços e aplicativos em interação.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-146">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="e4bc6-147">Este guia é um complemento do ["_Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres_"](../microservices-architecture/index.md) que se concentra mais no Docker, em microsserviços e na implantação de contêineres para hospedar aplicativos empresariais.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-147">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="e4bc6-148">Microsserviços do .NET.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-148">.NET Microservices.</span></span> <span data-ttu-id="e4bc6-149">Arquitetura de aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="e4bc6-149">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="e4bc6-150">**livro eletrônico**</span><span class="sxs-lookup"><span data-stu-id="e4bc6-150">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="e4bc6-151">**Aplicativo de exemplo**</span><span class="sxs-lookup"><span data-stu-id="e4bc6-151">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="e4bc6-152">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="e4bc6-152">Who should use this guide</span></span>

<span data-ttu-id="e4bc6-153">O público-alvo principal deste guia são desenvolvedores, líderes de desenvolvimento e arquitetos interessados em compilar aplicativos Web modernos usando tecnologias e serviços da Microsoft na nuvem.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-153">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="e4bc6-154">Um público-alvo secundário são os tomadores de decisões técnicas que já estão familiarizados com o ASP.NET ou com o Azure e estão buscando informações para saber se é interessante atualizar seus projetos novos ou existentes para o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-154">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="e4bc6-155">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="e4bc6-155">How you can use this guide</span></span>

<span data-ttu-id="e4bc6-156">Este guia foi condensado em um documento relativamente pequeno que se concentra na compilação de aplicativos Web com tecnologias .NET modernas e o Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-156">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="e4bc6-157">Como tal, ele pode ser lido em sua totalidade para fornecer uma base de compreensão desses aplicativos e suas considerações técnicas.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-157">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="e4bc6-158">O guia, junto com seu aplicativo de exemplo, também pode servir como um ponto de partida ou de referência.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-158">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="e4bc6-159">Use o aplicativo de exemplo associado como um modelo para seus próprios aplicativos ou para ver como você poderia organizar os blocos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-159">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="e4bc6-160">Confira os princípios do guia, a cobertura das opções de arquitetura e de tecnologia e as considerações de decisões ao ponderar essas opções para seu próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-160">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="e4bc6-161">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-161">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="e4bc6-162">Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="e4bc6-162">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="e4bc6-163">Referências</span><span class="sxs-lookup"><span data-stu-id="e4bc6-163">References</span></span>

- <span data-ttu-id="e4bc6-164">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="e4bc6-164">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="e4bc6-165">Avançar</span><span class="sxs-lookup"><span data-stu-id="e4bc6-165">Next</span></span>](modern-web-applications-characteristics.md)