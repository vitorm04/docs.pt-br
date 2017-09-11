---
title: "Programação com domínios do aplicativo e assemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6dcf8e4c9bf2401309b1d80d2306bd619b96460d
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="08934-102">Programação com domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="08934-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="08934-103">Os hosts como Microsoft Internet Explorer, ASP.NET e o shell do Windows carregam o Common Language Runtime em um processo, criam um [domínio do aplicativo](../../../docs/framework/app-domains/application-domains.md) nesse processo e, em seguida, carregam e executam código de usuário nesse domínio do aplicativo ao executar um aplicativo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08934-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="08934-104">Na maioria dos casos, você não precisa se preocupar em criar domínios do aplicativo nem em carregar assemblies neles, pois o host de tempo de execução executa essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="08934-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="08934-105">No entanto, se estiver criando um aplicativo que hospedará o Common Language Runtime, criando ferramentas ou código que deseja descarregar de modo programático, ou criando componentes conectáveis que podem ser descarregados e recarregados dinamicamente, você estará criando seus próprios domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08934-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="08934-106">Mesmo se não estiver criando um host de tempo de execução, esta seção fornece informações importantes sobre como trabalhar com domínios do aplicativo e assemblies carregados nesses domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08934-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08934-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="08934-107">In This Section</span></span>  
 [<span data-ttu-id="08934-108">Tópicos explicativos sobre domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="08934-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="08934-109">Fornece links a todos os Tópicos explicativos encontrados na documentação conceitual para programação com domínios do aplicativo e assemblies.</span><span class="sxs-lookup"><span data-stu-id="08934-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="08934-110">Usando domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="08934-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="08934-111">Fornece exemplos de como criar, configurar e usar domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08934-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="08934-112">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="08934-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="08934-113">Descreve como criar, assinar e definir atributos em assemblies.</span><span class="sxs-lookup"><span data-stu-id="08934-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08934-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="08934-114">Related Sections</span></span>  
 [<span data-ttu-id="08934-115">Emissão de métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="08934-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="08934-116">Descreve como criar assemblies dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="08934-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="08934-117">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="08934-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="08934-118">Fornece uma visão geral conceitual de assemblies.</span><span class="sxs-lookup"><span data-stu-id="08934-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="08934-119">Domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="08934-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="08934-120">Fornece uma visão geral conceitual de domínios de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="08934-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="08934-121">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="08934-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="08934-122">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="08934-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>

