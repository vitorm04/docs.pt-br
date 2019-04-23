---
title: Esquema de configurações Web
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 1f0241b65c915dd5703ceea97dd5b07f88832003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113055"
---
# <a name="web-settings-schema"></a><span data-ttu-id="16559-102">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="16559-102">Web Settings Schema</span></span>
<span data-ttu-id="16559-103">As configurações de Web especificam as configurações do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="16559-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="16559-104">Essas configurações são diferentes das configurações de tipo de domínio do aplicativo que são especificadas no arquivo Web.config de um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="16559-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="16559-105">As configurações da Web estão contidas em arquivos Aspnet.config, que estão localizados nas pastas de instalação das versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16559-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="16559-106">Por exemplo, o arquivo Aspnet.config para [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] está na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="16559-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="16559-107">As configurações da Web não são usadas em nenhum outro arquivo de configuração, como o arquivo machine.config, o Web.config raiz ou os arquivos Web.config do nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16559-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="16559-108">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="16559-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 <span data-ttu-id="16559-109">[\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md) [Elemento system.web> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="16559-109">[\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)</span></span>  
  
 <span data-ttu-id="16559-110">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]</span><span class="sxs-lookup"><span data-stu-id="16559-110">[\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)</span></span>  
  
|<span data-ttu-id="16559-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="16559-111">Element</span></span>|<span data-ttu-id="16559-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="16559-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16559-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="16559-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="16559-114">Contém informações que a camada de hospedagem do ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="16559-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="16559-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="16559-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="16559-116">Especifica as configurações de CPU e do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="16559-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16559-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16559-117">See also</span></span>

- [<span data-ttu-id="16559-118">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="16559-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
