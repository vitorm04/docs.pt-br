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
ms.openlocfilehash: c3ac9b42aeff3f7b26f0b36480bc75ceda39e7e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185594"
---
# <a name="web-settings-schema"></a><span data-ttu-id="67fbc-102">Esquema de configurações Web</span><span class="sxs-lookup"><span data-stu-id="67fbc-102">Web Settings Schema</span></span>

<span data-ttu-id="67fbc-103">As configurações de Web especificam as configurações do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67fbc-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="67fbc-104">Essas configurações são diferentes das configurações de tipo de domínio do aplicativo que são especificadas no arquivo Web.config de um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67fbc-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="67fbc-105">As configurações da Web estão contidas em arquivos Aspnet.config, que estão localizados nas pastas de instalação das versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67fbc-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="67fbc-106">Por exemplo, o arquivo de Aspnet.config para .NET Framework 2,0 está na seguinte pasta:</span><span class="sxs-lookup"><span data-stu-id="67fbc-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="67fbc-107">As configurações da Web não são usadas em nenhum outro arquivo de configuração, como o arquivo machine.config, o Web.config raiz ou os arquivos Web.config do nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="67fbc-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="67fbc-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="67fbc-108">Element</span></span>|<span data-ttu-id="67fbc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="67fbc-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="67fbc-110">Contém informações que a camada de hospedagem do ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="67fbc-110">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="67fbc-111">Especifica as configurações de CPU e do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="67fbc-111">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67fbc-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="67fbc-112">See also</span></span>

- [<span data-ttu-id="67fbc-113">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="67fbc-113">Configuration File Schema</span></span>](../index.md)
