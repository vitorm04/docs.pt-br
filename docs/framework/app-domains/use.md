---
title: "Usando domínios do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53180d5d3d9314c3f078ddca8f5c155b01981f4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-domains"></a><span data-ttu-id="ad7a3-102">Usando domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-102">Using Application Domains</span></span>
<span data-ttu-id="ad7a3-103">Os domínios do aplicativos fornecem uma unidade de isolamento para o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="ad7a3-104">Eles são criados e executados dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-104">They are created and run inside a process.</span></span> <span data-ttu-id="ad7a3-105">Domínios do aplicativo geralmente são criados por um host de tempo de execução, que é um aplicativo responsável por carregar o tempo de execução para um processo e executar o código do usuário em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="ad7a3-106">O host de tempo de execução cria um processo e um domínio de aplicativo padrão e executa o código gerenciado dentro dele.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="ad7a3-107">Hosts de tempo de execução incluem ASP.NET, Microsoft Internet Explorer e o shell do Windows.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="ad7a3-108">Para a maioria dos aplicativos, você não precisará criar seu próprio domínio do aplicativo; o host de tempo de execução cria os domínios do aplicativo necessários para você.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="ad7a3-109">No entanto, você pode criar e configurar domínios do aplicativo adicionais se seu aplicativo precisar isolar o código ou usar e descarregar DLLs.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad7a3-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ad7a3-110">In This Section</span></span>  
 [<span data-ttu-id="ad7a3-111">Como criar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="ad7a3-112">Descreve como criar um domínio do aplicativo com programação.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="ad7a3-113">Como descarregar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="ad7a3-114">Descreve como descarregar um domínio do aplicativo com programação.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="ad7a3-115">Como configurar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="ad7a3-116">Fornece uma introdução à configuração de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="ad7a3-117">Recuperação de informações de instalação de um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="ad7a3-118">Descreve como recuperar informações de configuração de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="ad7a3-119">Como carregar assemblies em um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="ad7a3-120">Descreve como carregar um assembly em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="ad7a3-121">Como obter as informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="ad7a3-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="ad7a3-122">Descreve como recuperar informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="ad7a3-123">Cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="ad7a3-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="ad7a3-124">Descreve como a cópia de sombra permite realizar atualizações nos assemblies enquanto eles estão em uso e como configurar cópias de sombra.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="ad7a3-125">Como receber notificações de exceção de primeira tentativa</span><span class="sxs-lookup"><span data-stu-id="ad7a3-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="ad7a3-126">Explica como você pode receber uma notificação de que uma exceção foi gerada, antes do Common Language Runtime começar a procurar por manipuladores de exceção.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="ad7a3-127">Como resolver carregamentos de assembly</span><span class="sxs-lookup"><span data-stu-id="ad7a3-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="ad7a3-128">Fornece diretrizes sobre como usar o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> para resolver falhas de carregamento de assembly.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ad7a3-129">Referência</span><span class="sxs-lookup"><span data-stu-id="ad7a3-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="ad7a3-130">Representa um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-130">Represents an application domain.</span></span> <span data-ttu-id="ad7a3-131">Fornece métodos para criar e controlar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad7a3-132">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ad7a3-132">Related Sections</span></span>  
 [<span data-ttu-id="ad7a3-133">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="ad7a3-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="ad7a3-134">Fornece uma visão geral das funções executadas por assemblies.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="ad7a3-135">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="ad7a3-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="ad7a3-136">Descreve como criar, assinar e definir atributos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="ad7a3-137">Emissão de métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="ad7a3-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="ad7a3-138">Descreve como criar assemblies dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="ad7a3-139">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ad7a3-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="ad7a3-140">Fornece uma visão geral conceitual de domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="ad7a3-141">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="ad7a3-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="ad7a3-142">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="ad7a3-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
