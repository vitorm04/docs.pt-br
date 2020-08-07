---
title: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
description: Obtenha uma visão geral de alto nível do processo de desenvolvimento e implantação para desenvolver e implantar aplicativos em contêineres com o Docker e a plataforma e as ferramentas da Microsoft.
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915160"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="86f8a-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)</span><span class="sxs-lookup"><span data-stu-id="86f8a-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Capa do livro](./media/devops-book-cover-large-we.png)

<span data-ttu-id="86f8a-105">**Edição v 3.1** -atualizado para ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="86f8a-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="86f8a-106">Este guia é uma visão geral para desenvolver e implantar aplicativos ASP.NET Core em contêineres com o Docker, usando a plataforma e as ferramentas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86f8a-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="86f8a-107">O guia inclui uma introdução de alto nível ao Azure DevOps, para implementar pipelines de CI/CD, bem como o ACR (registro de contêiner do Azure) e os serviços Kubernetess do Azure AKS para implantação.</span><span class="sxs-lookup"><span data-stu-id="86f8a-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="86f8a-108">Para obter detalhes relacionados ao desenvolvimento de baixo nível, você pode ver o guia [microservices do .net: arquitetura para aplicativos em contêineres .net](https://docs.microsoft.com/dotnet/architecture/microservices/) e o aplicativo de referência relacionado [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="86f8a-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="86f8a-109">Envie-nos seus comentários!</span><span class="sxs-lookup"><span data-stu-id="86f8a-109">Send us your feedback!</span></span>

<span data-ttu-id="86f8a-110">Escrevemos este guia para ajudá-lo a entender a arquitetura de aplicativos em contêineres e de microsserviços no .NET.</span><span class="sxs-lookup"><span data-stu-id="86f8a-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="86f8a-111">O guia e o aplicativo de referência relacionado continuarão sendo desenvolvidos, portanto seus comentários são bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="86f8a-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="86f8a-112">Se você tiver comentários sobre como esse guia pode ser melhorado, envie comentários em <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="86f8a-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="86f8a-113">Credits</span><span class="sxs-lookup"><span data-stu-id="86f8a-113">Credits</span></span>

<span data-ttu-id="86f8a-114">Autor:</span><span class="sxs-lookup"><span data-stu-id="86f8a-114">Author:</span></span>

> <span data-ttu-id="86f8a-115">**Cesar de la Torre**, Gerente sênior de produtos , equipe de produto do .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="86f8a-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="86f8a-116">Editor de aquisições:</span><span class="sxs-lookup"><span data-stu-id="86f8a-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="86f8a-117">**Janine Patrick**</span><span class="sxs-lookup"><span data-stu-id="86f8a-117">**Janine Patrick**</span></span>

<span data-ttu-id="86f8a-118">Editor de desenvolvimento:</span><span class="sxs-lookup"><span data-stu-id="86f8a-118">Developmental Editor:</span></span>

> <span data-ttu-id="86f8a-119">**Bob Russell**, profissional de soluções na Microsoft</span><span class="sxs-lookup"><span data-stu-id="86f8a-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="86f8a-120">**Publicação octal, Inc.**</span><span class="sxs-lookup"><span data-stu-id="86f8a-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="86f8a-121">Produção editorial:</span><span class="sxs-lookup"><span data-stu-id="86f8a-121">Editorial Production:</span></span>

> [<span data-ttu-id="86f8a-122">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="86f8a-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="86f8a-123">**Publicação octal, Inc.**</span><span class="sxs-lookup"><span data-stu-id="86f8a-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="86f8a-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="86f8a-124">Copyeditor:</span></span>

> <span data-ttu-id="86f8a-125">**Bob Russell**, profissional de soluções na Microsoft</span><span class="sxs-lookup"><span data-stu-id="86f8a-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="86f8a-126">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="86f8a-126">Participants and reviewers:</span></span>

> <span data-ttu-id="86f8a-127">**Nish Anil**, Gerente de Programa Sênior, Equipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="86f8a-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="86f8a-128">**Miguel Veloso**, engenheiro de desenvolvimento de software em conceitos simples</span><span class="sxs-lookup"><span data-stu-id="86f8a-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="86f8a-129">**Pedro Ghosh**, consultor principal da Neudesic</span><span class="sxs-lookup"><span data-stu-id="86f8a-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="86f8a-130">Direitos autorais</span><span class="sxs-lookup"><span data-stu-id="86f8a-130">Copyright</span></span>

<span data-ttu-id="86f8a-131">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="86f8a-131">PUBLISHED BY</span></span>

<span data-ttu-id="86f8a-132">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86f8a-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="86f8a-133">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="86f8a-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="86f8a-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="86f8a-134">One Microsoft Way</span></span>

<span data-ttu-id="86f8a-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="86f8a-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="86f8a-136">Copyright &copy; 2020 da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="86f8a-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="86f8a-137">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="86f8a-137">All rights reserved.</span></span> <span data-ttu-id="86f8a-138">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="86f8a-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="86f8a-139">Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="86f8a-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="86f8a-140">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="86f8a-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="86f8a-141"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="86f8a-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="86f8a-142">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="86f8a-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="86f8a-143">A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86f8a-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="86f8a-144">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="86f8a-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="86f8a-145">O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.</span><span class="sxs-lookup"><span data-stu-id="86f8a-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="86f8a-146">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="86f8a-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="86f8a-147">Próximo</span><span class="sxs-lookup"><span data-stu-id="86f8a-147">Next</span></span>](introduction-to-containers-and-docker.md)
