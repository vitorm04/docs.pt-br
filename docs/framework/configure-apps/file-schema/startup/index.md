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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078156"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="feb6a-102">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="feb6a-102">Startup Settings Schema</span></span>
<span data-ttu-id="feb6a-103">As configurações de inicialização especificam a versão do Common Language Runtime que deve executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="feb6a-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="feb6a-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="feb6a-104">Element</span></span>|<span data-ttu-id="feb6a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="feb6a-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="feb6a-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="feb6a-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="feb6a-107">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="feb6a-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="feb6a-108">Os aplicativos criados com a versão 1.1 do tempo de execução devem usar o elemento **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="feb6a-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="feb6a-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="feb6a-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="feb6a-110">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="feb6a-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="feb6a-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="feb6a-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="feb6a-112">Contém os elementos **\<requiredRuntime>** e **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="feb6a-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="feb6a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb6a-113">See Also</span></span>  
 [<span data-ttu-id="feb6a-114">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="feb6a-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 <span data-ttu-id="feb6a-115">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)</span><span class="sxs-lookup"><span data-stu-id="feb6a-115">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)</span></span>
