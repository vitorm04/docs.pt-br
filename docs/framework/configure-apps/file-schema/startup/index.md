---
title: "Esquema de configurações de inicialização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="858e2-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="858e2-102">Startup Settings Schema</span></span>
<span data-ttu-id="858e2-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="858e2-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="858e2-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="858e2-104">Element</span></span>|<span data-ttu-id="858e2-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="858e2-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="858e2-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="858e2-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="858e2-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="858e2-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="858e2-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="858e2-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="858e2-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="858e2-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="858e2-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="858e2-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="858e2-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="858e2-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="858e2-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="858e2-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="858e2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="858e2-113">See Also</span></span>  
 [<span data-ttu-id="858e2-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="858e2-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 <span data-ttu-id="858e2-115">[\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)</span><span class="sxs-lookup"><span data-stu-id="858e2-115">[\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)</span></span>
