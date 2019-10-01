---
title: Documentação do .NET Framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699050"
---
# <a name="net-framework-guide"></a><span data-ttu-id="1212d-102">Guia do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1212d-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="1212d-103">Este conjunto de conteúdo do .NET Framework inclui informações para versões do .NET Framework 4.5 e 4.8.</span><span class="sxs-lookup"><span data-stu-id="1212d-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="1212d-104">Para baixar o .NET Framework, confira [Instalando o .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="1212d-105">Para obter uma lista de novos recursos e alterações no .NET Framework, consulte [Novidades no .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="1212d-106">Para obter uma lista de plataformas com suporte, confira [Requisitos do sistema .NET Framework](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="1212d-107">Para obter a documentação sobre versões antigas do .NET Framework, consulte a [documentação de versões anteriores do .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="1212d-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="1212d-108">O .NET Framework é uma plataforma de desenvolvimento para criar aplicativos para web, Windows, Windows Phone, Windows Server e Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="1212d-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="1212d-109">Ele consiste no Common Language Runtime (CLR) e na biblioteca de classes do .NET Framework, que inclui uma ampla gama de recursos e suporte para muitos padrões do setor.</span><span class="sxs-lookup"><span data-stu-id="1212d-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="1212d-110">O .NET Framework fornece vários serviços, incluindo gerenciamento de memória, segurança de tipo e memória, segurança, redes e implantação de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1212d-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="1212d-111">Ele fornece APIs e estruturas de dados fáceis de usam que abstraem o sistema operacional do Windows.</span><span class="sxs-lookup"><span data-stu-id="1212d-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="1212d-112">Você pode usar diferentes linguagens de programação com o .NET Framework, incluindo C#, F# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1212d-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="1212d-113">Para obter uma introdução geral ao .NET Framework para usuários e desenvolvedores, veja [Introdução](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="1212d-114">Para obter uma introdução à arquitetura e aos recursos principais do .NET Framework, confira a [visão geral](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="1212d-115">O .NET Framework pode ser usado com o Docker e com [Contêineres do Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="1212d-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="1212d-116">Instalação</span><span class="sxs-lookup"><span data-stu-id="1212d-116">Installation</span></span>

<span data-ttu-id="1212d-117">O .NET Framework vem com o Windows, permitindo que você execute aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="1212d-118">Pode ser necessário ter uma versão do .NET Framework posterior àquela fornecida com sua versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="1212d-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="1212d-119">Para saber mais, confira [Instalar o .NET Framework no Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="1212d-120">Consulte [Reparar o .NET Framework](./install/repair.md) para saber como reparar sua instalação do .NET Framework caso esteja vendo erros durante a instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="1212d-121">Para obter mais informações detalhadas sobre como baixar o .NET Framework, confira [Instalar o .NET Framework para desenvolvedores](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="1212d-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1212d-122">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1212d-122">In this section</span></span>

* [<span data-ttu-id="1212d-123">Novidades</span><span class="sxs-lookup"><span data-stu-id="1212d-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="1212d-124">Descreve novos recursos e alterações principais nas versões mais recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="1212d-125">Inclui listas de tipos e membros obsoletos e fornece um guia para migrar seus aplicativos da versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="1212d-126">Introdução</span><span class="sxs-lookup"><span data-stu-id="1212d-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="1212d-127">Fornece uma visão geral abrangente do .NET Framework e links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="1212d-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="1212d-128">Guia de instalação</span><span class="sxs-lookup"><span data-stu-id="1212d-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="1212d-129">Fornece recursos e orientações sobre a instalação e a solução de problemas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="1212d-130">Guia de migração</span><span class="sxs-lookup"><span data-stu-id="1212d-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="1212d-131">Fornece recursos e uma lista de alterações que você precisa considerar se estiver migrando seu aplicativo para uma nova versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="1212d-132">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="1212d-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="1212d-133">Fornece um guia para todas as principais áreas de tecnologia e tarefas para o desenvolvimento de aplicativos, incluindo a criação, a configuração, a depuração, a proteção e a implantação de seu aplicativo, bem como informações sobre programação dinâmica, interoperabilidade, extensibilidade, gerenciamento de memória e threading.</span><span class="sxs-lookup"><span data-stu-id="1212d-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="1212d-134">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="1212d-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="1212d-135">Descreve as ferramentas que ajudam você a desenvolver, configurar e implantar aplicativos usando tecnologias do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1212d-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="1212d-136">APIs e bibliotecas de classes adicionais</span><span class="sxs-lookup"><span data-stu-id="1212d-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="1212d-137">Fornece documentação para APIs privadas do .NET Framework usadas pelas ferramentas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1212d-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="1212d-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1212d-138">See also</span></span>

- [<span data-ttu-id="1212d-139">Biblioteca de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1212d-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
