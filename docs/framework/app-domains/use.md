---
title: Usando domínios do aplicativo
description: Use domínios de aplicativo, que fornecem uma unidade de isolamento para o Common Language Runtime (CLR). Os domínios de aplicativo são criados e executados dentro de um processo.
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: df2a63716904ebfc6ee163121a1f07e53aa07514
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105181"
---
# <a name="using-application-domains"></a><span data-ttu-id="633eb-104">Usando domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-104">Using Application Domains</span></span>

<span data-ttu-id="633eb-105">Os domínios do aplicativos fornecem uma unidade de isolamento para o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="633eb-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="633eb-106">Eles são criados e executados dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="633eb-106">They are created and run inside a process.</span></span> <span data-ttu-id="633eb-107">Domínios do aplicativo geralmente são criados por um host de runtime, que é um aplicativo responsável por carregar o runtime para um processo e executar o código do usuário em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="633eb-108">O host de runtime cria um processo e um domínio de aplicativo padrão e executa o código gerenciado dentro dele.</span><span class="sxs-lookup"><span data-stu-id="633eb-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="633eb-109">Hosts de runtime incluem ASP.NET, Microsoft Internet Explorer e o shell do Windows.</span><span class="sxs-lookup"><span data-stu-id="633eb-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="633eb-110">Para a maioria dos aplicativos, você não precisará criar seu próprio domínio do aplicativo; o host de runtime cria os domínios do aplicativo necessários para você.</span><span class="sxs-lookup"><span data-stu-id="633eb-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="633eb-111">No entanto, você pode criar e configurar domínios do aplicativo adicionais se seu aplicativo precisar isolar o código ou usar e descarregar DLLs.</span><span class="sxs-lookup"><span data-stu-id="633eb-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="633eb-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="633eb-112">In This Section</span></span>  

[<span data-ttu-id="633eb-113">Como: Criar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="633eb-114">Descreve como criar um domínio do aplicativo com programação.</span><span class="sxs-lookup"><span data-stu-id="633eb-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="633eb-115">Como: Descarregar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="633eb-116">Descreve como descarregar um domínio do aplicativo com programação.</span><span class="sxs-lookup"><span data-stu-id="633eb-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="633eb-117">Como: Configurar um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="633eb-118">Fornece uma introdução à configuração de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="633eb-119">Recuperando informações de instalação de um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="633eb-120">Descreve como recuperar informações de configuração de um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="633eb-121">Como: Carregar assemblies em um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="633eb-122">Descreve como carregar um assembly em um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="633eb-123">Como obter as informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="633eb-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="633eb-124">Descreve como recuperar informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="633eb-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="633eb-125">Criando cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="633eb-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="633eb-126">Descreve como a cópia de sombra permite realizar atualizações nos assemblies enquanto eles estão em uso e como configurar cópias de sombra.</span><span class="sxs-lookup"><span data-stu-id="633eb-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="633eb-127">Como: Receber notificações de exceção de primeira tentativa</span><span class="sxs-lookup"><span data-stu-id="633eb-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="633eb-128">Explica como você pode receber uma notificação de que uma exceção foi gerada, antes do Common Language Runtime começar a procurar por manipuladores de exceção.</span><span class="sxs-lookup"><span data-stu-id="633eb-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="633eb-129">Como resolver carregamentos de assembly</span><span class="sxs-lookup"><span data-stu-id="633eb-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="633eb-130">Fornece diretrizes sobre como usar o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> para resolver falhas de carregamento de assembly.</span><span class="sxs-lookup"><span data-stu-id="633eb-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="633eb-131">Referência</span><span class="sxs-lookup"><span data-stu-id="633eb-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="633eb-132">Representa um domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-132">Represents an application domain.</span></span> <span data-ttu-id="633eb-133">Fornece métodos para criar e controlar domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="633eb-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="633eb-134">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="633eb-134">Related Sections</span></span>  
[<span data-ttu-id="633eb-135">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="633eb-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="633eb-136">Fornece uma visão geral das funções executadas por assemblies.</span><span class="sxs-lookup"><span data-stu-id="633eb-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="633eb-137">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="633eb-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="633eb-138">Descreve como criar, assinar e definir atributos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="633eb-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="633eb-139">Emissão de métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="633eb-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="633eb-140">Descreve como criar assemblies dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="633eb-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="633eb-141">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="633eb-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="633eb-142">Fornece uma visão geral conceitual de domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="633eb-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="633eb-143">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="633eb-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="633eb-144">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="633eb-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
