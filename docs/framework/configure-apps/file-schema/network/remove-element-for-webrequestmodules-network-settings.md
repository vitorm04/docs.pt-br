---
title: '&lt;remover&gt; elemento para webRequestModules (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d0da0fd2edae4687ea80b4a23cc82a25ead9cb7b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208575"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a>&lt;remover&gt; elemento para webRequestModules (configurações de rede)
Remove um módulo de solicitação da Web personalizado do aplicativo.  
  
 \<configuration>  
\<system.net>  
\<webRequestModules >  
\<remove>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`prefix`|O prefixo URI para solicitações manipuladas por esse módulo de solicitação da Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Especifica os módulos para usá-lo para solicitar informações de hosts da rede.|  
  
## <a name="remarks"></a>Comentários  
 O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo URI especificado.  
  
 O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "http", ou "`http://www.contoso.com` ".  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e, em seguida, registra um novo módulo de solicitação da Web personalizado para solicitações HTTP para www.contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.WebRequest>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
