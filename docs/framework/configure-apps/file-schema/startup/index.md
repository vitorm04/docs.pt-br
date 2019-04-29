---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701509"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="04818-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="04818-102">Startup settings schema</span></span>

<span data-ttu-id="04818-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04818-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="04818-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="04818-104">Element</span></span>|<span data-ttu-id="04818-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="04818-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04818-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="04818-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="04818-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="04818-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="04818-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="04818-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="04818-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="04818-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="04818-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="04818-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="04818-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="04818-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="04818-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="04818-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04818-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04818-113">See also</span></span>

- [<span data-ttu-id="04818-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="04818-114">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="04818-115">Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores</span><span class="sxs-lookup"><span data-stu-id="04818-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
