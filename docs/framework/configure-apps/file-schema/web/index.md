---
title: "Esquema de configurações Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="web-settings-schema"></a>Esquema de configurações Web
As configurações de Web especificam as configurações do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET. Essas configurações são diferentes das configurações de tipo de domínio do aplicativo que são especificadas no arquivo Web.config de um aplicativo ASP.NET.  
  
 As configurações da Web estão contidas em arquivos Aspnet.config, que estão localizados nas pastas de instalação das versões do .NET Framework. Por exemplo, o arquivo Aspnet.config para [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] está na seguinte pasta:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 As configurações da Web não são usadas em nenhum outro arquivo de configuração, como o arquivo machine.config, o Web.config raiz ou os arquivos Web.config do nível do aplicativo.  
  
 [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md) [Elemento system.web> (configurações da Web)]  
  
 [\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contém informações que a camada de hospedagem do ASP.NET usa.|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Especifica as configurações de CPU e do ASP.NET em nível de execução que se aplicam ao comportamento de todo o processo gerenciado pela camada de hospedagem do ASP.NET.|  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
