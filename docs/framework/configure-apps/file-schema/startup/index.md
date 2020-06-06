---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701509"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="64134-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="64134-102">Startup settings schema</span></span>

<span data-ttu-id="64134-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="64134-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="64134-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="64134-104">Element</span></span>|<span data-ttu-id="64134-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="64134-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="64134-106">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="64134-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="64134-107">Os aplicativos criados com a versão de tempo de execução 1,1 devem usar o **\<supportedRuntime>** elemento.</span><span class="sxs-lookup"><span data-stu-id="64134-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="64134-108">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="64134-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="64134-109">Contém os **\<requiredRuntime>** **\<supportedRuntime>** elementos e.</span><span class="sxs-lookup"><span data-stu-id="64134-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64134-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="64134-110">See also</span></span>

- [<span data-ttu-id="64134-111">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="64134-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="64134-112">Como configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="64134-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
