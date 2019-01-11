---
title: Esquema de configurações de inicialização
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0a03438968f487f574606f415fb9d43223030038
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222149"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="ab0a4-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="ab0a4-102">Startup settings schema</span></span>

<span data-ttu-id="ab0a4-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ab0a4-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="ab0a4-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab0a4-104">Element</span></span>|<span data-ttu-id="ab0a4-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab0a4-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab0a4-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="ab0a4-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="ab0a4-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ab0a4-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ab0a4-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="ab0a4-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="ab0a4-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="ab0a4-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="ab0a4-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="ab0a4-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="ab0a4-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="ab0a4-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="ab0a4-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="ab0a4-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab0a4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab0a4-113">See also</span></span>

- [<span data-ttu-id="ab0a4-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ab0a4-114">Configuration File Schema</span></span>](../index.md)  
- [<span data-ttu-id="ab0a4-115">Como: Configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ab0a4-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)