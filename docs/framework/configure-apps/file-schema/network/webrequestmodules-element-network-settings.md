---
title: '&lt;webRequestModules&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7454099d8af0f2d656296be55677c648cc0c36c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742686"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;webRequestModules&gt; elemento (configurações de rede)
Especifica módulos a ser usado para solicitar informações de hosts de rede.  
  
 \<configuration>  
\<system.net>  
\<webRequestModules >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Adiciona um módulo de solicitação da Web personalizado para o aplicativo.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Remove todos os módulos de solicitação da Web registrados do aplicativo.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Remove um módulo personalizado de solicitação da Web do aplicativo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
 O `webRequestModules` descendentes do elemento registra o <xref:System.Net.WebRequest> classe para manipular solicitações de informações aos hosts de rede. Módulos de solicitação da Web devem implementar o <xref:System.Net.IWebRequestCreate> interface.  
  
 O .NET Framework inclui módulos de solicitação da Web para URIs que começam com http://, https:// e file://. Você pode substituir os módulos padrão somente por registrar um módulo personalizado no arquivo de configuração.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra o módulo HTTP padrão. Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
 <xref:System.Net.IWebRequestCreate>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
