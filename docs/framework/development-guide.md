---
title: Guia de Desenvolvimento do .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429eae61ab311d2a7a68567c97f40e1fdc0a1f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="6beed-102">Guia de Desenvolvimento do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6beed-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="6beed-103">Esta seção explica como criar, configurar, depurar, proteger e implantar aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="6beed-104">Esta seção também fornece informações sobre áreas de tecnologia como programação dinâmica, interoperabilidade, extensibilidade, gerenciamento de memória e threading.</span><span class="sxs-lookup"><span data-stu-id="6beed-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6beed-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6beed-105">In This Section</span></span>  
 [<span data-ttu-id="6beed-106">Fundamentos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6beed-106">Application Essentials</span></span>](../../docs/standard/application-essentials.md)  
 <span data-ttu-id="6beed-107">Fornece informações sobre tarefas básicas de desenvolvimento de aplicativo como programação com domínios e assemblies de aplicativo, uso de atributos, tipos base de formatação e análise, uso de coleções, manipulação de eventos e exceções, uso de fluxos de arquivos e dados e uso de genéricos.</span><span class="sxs-lookup"><span data-stu-id="6beed-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="6beed-108">Dados e modelagem</span><span class="sxs-lookup"><span data-stu-id="6beed-108">Data and Modeling</span></span>](../../docs/framework/data/index.md)  
 <span data-ttu-id="6beed-109">Fornece informações sobre como acessar dados usando ADO.NET, Language Integrated Query (LINQ), WCF Data Services e XML.</span><span class="sxs-lookup"><span data-stu-id="6beed-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="6beed-110">Aplicativos cliente</span><span class="sxs-lookup"><span data-stu-id="6beed-110">Client Applications</span></span>](../../docs/framework/develop-client-apps.md)  
 <span data-ttu-id="6beed-111">Explica como criar aplicativos baseados em Windows usando o Windows Presentation Foundation (WPF) ou o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6beed-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="6beed-112">Aplicativos Web com o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6beed-112">Web Applications with ASP.NET</span></span>](../../docs/framework/develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="6beed-113">Fornece links para informações sobre como usar o ASP.NET para compilar aplicativos Web de classe corporativa com um mínimo de codificação.</span><span class="sxs-lookup"><span data-stu-id="6beed-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="6beed-114">Aplicativos orientados a serviços com WCF</span><span class="sxs-lookup"><span data-stu-id="6beed-114">Service-Oriented Applications with WCF</span></span>](../../docs/framework/wcf/index.md)  
 <span data-ttu-id="6beed-115">Descreve como usar o Windows Communication Foundation (WCF) para compilar aplicativos orientados a serviços, seguros e confiáveis.</span><span class="sxs-lookup"><span data-stu-id="6beed-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="6beed-116">[Criando fluxos de trabalho com o Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="6beed-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="6beed-117">Fornece informações sobre o modelo de programação, os exemplos e as ferramentas para usar o Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="6beed-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="6beed-118">Aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="6beed-118">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
 <span data-ttu-id="6beed-119">Explica como é possível usar o Visual Studio e o .NET Framework para criar um aplicativo que é instalado como um serviço e, iniciar, parar e de outro modo controlar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="6beed-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="6beed-120">Processamento paralelo e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="6beed-120">Parallel Processing and Concurrency</span></span>](../../docs/standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="6beed-121">Fornece informações sobre padrões de design de threading gerenciado, programação paralela e programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6beed-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="6beed-122">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6beed-122">Network Programming in the .NET Framework</span></span>](../../docs/framework/network-programming/index.md)  
 <span data-ttu-id="6beed-123">Descreve a implementação gerenciada, extensível e em camadas de serviços da Internet que podem ser integrados a aplicativos de maneira fácil e rápida.</span><span class="sxs-lookup"><span data-stu-id="6beed-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="6beed-124">[Configurando aplicativos .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="6beed-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="6beed-125">Explica como usar arquivos de configuração para alterar configurações sem ter que recompilar os aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="6beed-126">Compilação de aplicativos com o .NET Native</span><span class="sxs-lookup"><span data-stu-id="6beed-126">Compiling Apps with .NET Native</span></span>](../../docs/framework/net-native/index.md)  
 <span data-ttu-id="6beed-127">Explica como usar a tecnologia de pré-compilação [!INCLUDE[net_native](../../includes/net-native-md.md)] para compilar e implantar aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="6beed-127">Explains how you can use the [!INCLUDE[net_native](../../includes/net-native-md.md)] precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="6beed-128">O [!INCLUDE[net_native](../../includes/net-native-md.md)] compila aplicativos que são escritos em código gerenciado (C#) e que destinam o .NET Framework para código nativo.</span><span class="sxs-lookup"><span data-stu-id="6beed-128">[!INCLUDE[net_native](../../includes/net-native-md.md)] compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="6beed-129">Segurança</span><span class="sxs-lookup"><span data-stu-id="6beed-129">Security</span></span>](../../docs/standard/security/index.md)  
 <span data-ttu-id="6beed-130">Fornece informações sobre as classes e serviços no .NET Framework que facilitam o desenvolvimento de aplicativos seguros.</span><span class="sxs-lookup"><span data-stu-id="6beed-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="6beed-131">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6beed-131">Debugging, Tracing, and Profiling</span></span>](../../docs/framework/debug-trace-profile/index.md)  
 <span data-ttu-id="6beed-132">Explica como testar, otimizar e criar perfis de aplicativos .NET Framework e do ambiente de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6beed-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="6beed-133">Esta seção inclui informações para administradores e para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="6beed-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="6beed-134">Desenvolvimento para várias plataformas</span><span class="sxs-lookup"><span data-stu-id="6beed-134">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="6beed-135">Fornece informações sobre como usar o .NET Framework para compilar assemblies que podem ser compartilhados entre múltiplas plataformas e múltiplos dispositivos como celulares, desktops e Web.</span><span class="sxs-lookup"><span data-stu-id="6beed-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="6beed-136">Implantação</span><span class="sxs-lookup"><span data-stu-id="6beed-136">Deployment</span></span>](../../docs/framework/deployment/index.md)  
 <span data-ttu-id="6beed-137">Explica como empacotar e distribuir o aplicativo .NET Framework e inclui guias de implantação para desenvolvedores e administradores.</span><span class="sxs-lookup"><span data-stu-id="6beed-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="6beed-138">Desempenho</span><span class="sxs-lookup"><span data-stu-id="6beed-138">Performance</span></span>](../../docs/framework/performance/index.md)  
 <span data-ttu-id="6beed-139">Fornece informações sobre armazenamento em cache, inicialização ociosa, confiabilidade e eventos ETW.</span><span class="sxs-lookup"><span data-stu-id="6beed-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
  
 <!--zz [Advanced Reading for the .NET Framework](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)  
 Provides information about advanced development tasks and techniques in the .NET Framework, including extensibility, interoperability, and reflection. Also includes the reference topics for unmanaged APIs that can be used by managed apps, such as runtime hosts, compilers, disassemblers, debuggers, and profilers.  --> 
  
## <a name="reference"></a><span data-ttu-id="6beed-140">Referência</span><span class="sxs-lookup"><span data-stu-id="6beed-140">Reference</span></span>  
 [<span data-ttu-id="6beed-141">Biblioteca de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6beed-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="6beed-142">Fornece sintaxe, exemplos de código e informações de uso para cada classe contida nos namespaces [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6beed-142">Supplies syntax, code examples, and usage information for each class that is contained in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6beed-143">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6beed-143">Related Sections</span></span>  
 [<span data-ttu-id="6beed-144">Introdução</span><span class="sxs-lookup"><span data-stu-id="6beed-144">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
 <span data-ttu-id="6beed-145">Fornece uma visão geral abrangente do .NET Framework e links para recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="6beed-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="6beed-146">Novidades</span><span class="sxs-lookup"><span data-stu-id="6beed-146">What's New</span></span>](../../docs/framework/whats-new/index.md)  
 <span data-ttu-id="6beed-147">Descreve novos recursos e alterações principais na versão mais recente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="6beed-148">Inclui listas de tipos e membros novos e obsoletos e fornece um guia para migrar aplicativos da versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="6beed-149">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="6beed-149">Tools</span></span>](../../docs/framework/tools/index.md)  
 <span data-ttu-id="6beed-150">Descreve as ferramentas que ajudam a desenvolver, configurar e implantar aplicativos usando tecnologias do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="6beed-151">Exemplos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6beed-151">.NET Framework Samples</span></span>](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)  
 <span data-ttu-id="6beed-152">Fornece links para a Galeria de Exemplos de Código do MSDN com exemplos de aplicativos que demonstram tecnologias .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6beed-152">Provides links to the MSDN Code Samples Gallery for sample apps that demonstrate .NET Framework technologies.</span></span>
