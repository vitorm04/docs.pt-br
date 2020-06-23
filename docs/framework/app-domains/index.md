---
title: Programação com domínios do aplicativo e assemblies
description: Conheça a programação com domínios de aplicativo e assemblies no .NET. Consulte links para tópicos de instruções & exemplos sobre como criar domínios de aplicativo & assemblies.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903432"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="3bc5a-104">Programação com domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="3bc5a-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="3bc5a-105">Os hosts como Microsoft Internet Explorer, ASP.NET e o shell do Windows carregam o Common Language Runtime em um processo, criam um [domínio do aplicativo](application-domains.md) nesse processo e, em seguida, carregam e executam código de usuário nesse domínio do aplicativo ao executar um aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="3bc5a-106">Na maioria dos casos, você não precisa se preocupar em criar domínios do aplicativo nem em carregar assemblies neles, pois o host de runtime executa essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="3bc5a-107">No entanto, se estiver criando um aplicativo que hospedará o Common Language Runtime, criando ferramentas ou código que deseja descarregar de modo programático, ou criando componentes conectáveis que podem ser descarregados e recarregados dinamicamente, você estará criando seus próprios domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="3bc5a-108">Mesmo se não estiver criando um host de runtime, esta seção fornece informações importantes sobre como trabalhar com domínios do aplicativo e assemblies carregados nesses domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bc5a-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3bc5a-109">In This Section</span></span>  

[<span data-ttu-id="3bc5a-110">Tópicos explicativos sobre domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="3bc5a-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="3bc5a-111">Fornece links a todos os Tópicos explicativos encontrados na documentação conceitual para programação com domínios do aplicativo e assemblies.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="3bc5a-112">Usando domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3bc5a-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="3bc5a-113">Fornece exemplos de como criar, configurar e usar domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="3bc5a-114">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="3bc5a-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="3bc5a-115">Descreve como criar, assinar e definir atributos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3bc5a-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3bc5a-116">Related Sections</span></span>  

[<span data-ttu-id="3bc5a-117">Emissão de métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="3bc5a-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="3bc5a-118">Descreve como criar assemblies dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="3bc5a-119">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="3bc5a-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="3bc5a-120">Fornece uma visão geral conceitual de assemblies.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="3bc5a-121">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3bc5a-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="3bc5a-122">Fornece uma visão geral conceitual de domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="3bc5a-123">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="3bc5a-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="3bc5a-124">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="3bc5a-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
