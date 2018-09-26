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
ms.openlocfilehash: 4cdf6a051552ab1effd9c4d9c783297a62602f7a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204918"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="6aabb-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="6aabb-102">Startup Settings Schema</span></span>
<span data-ttu-id="6aabb-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6aabb-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="6aabb-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="6aabb-104">Element</span></span>|<span data-ttu-id="6aabb-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="6aabb-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aabb-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="6aabb-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="6aabb-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="6aabb-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="6aabb-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="6aabb-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="6aabb-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="6aabb-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="6aabb-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="6aabb-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="6aabb-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="6aabb-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="6aabb-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="6aabb-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6aabb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6aabb-113">See Also</span></span>  
 [<span data-ttu-id="6aabb-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6aabb-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 <span data-ttu-id="6aabb-115">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)</span><span class="sxs-lookup"><span data-stu-id="6aabb-115">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)</span></span>
