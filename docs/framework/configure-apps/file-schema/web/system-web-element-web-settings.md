---
title: '&lt;System. Web&gt; elemento (configurações da Web)'
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7527ee9e7528a0da47529bae93e8112705e03a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755156"
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System. Web&gt; elemento (configurações da Web)
Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento de todo o processo.  
  
 \<configuration>  
\<System. Web > elemento (configurações da Web)  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Especifica as configurações para pools de aplicativos do IIS em um arquivo ASPNET config.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Especifica o elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.|  
  
## <a name="remarks"></a>Comentários  
 O `system.web` elemento e seus filhos `applicationPool` elemento foram adicionados para o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] do [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia threads e como ele enfileira as solicitações ao ASP.NET hospedado em um pool de aplicativos do IIS. Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores no modo clássico ou ISAPI, essas configurações são ignoradas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o comportamento de todo o processo ASP.NET no arquivo ASPNET ao ASP.NET hospedado em um pool de aplicativos do IIS. O exemplo supõe que o IIS está em execução no integrado modo e que o aplicativo está usando o [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou uma versão posterior. Esse comportamento não ocorre nas versões do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] anteriores a [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Os valores de exemplo são os valores padrão.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|Namespace||  
|Nome do esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Consulte também  
 [\<applicationPool> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]
