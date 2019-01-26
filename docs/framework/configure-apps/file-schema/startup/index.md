---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083412"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="17245-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="17245-102">Startup settings schema</span></span>

<span data-ttu-id="17245-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17245-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="17245-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="17245-104">Element</span></span>|<span data-ttu-id="17245-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="17245-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17245-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="17245-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="17245-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="17245-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="17245-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="17245-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="17245-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="17245-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="17245-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="17245-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="17245-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="17245-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="17245-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="17245-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17245-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17245-113">See also</span></span>

- [<span data-ttu-id="17245-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="17245-114">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="17245-115">Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores</span><span class="sxs-lookup"><span data-stu-id="17245-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
