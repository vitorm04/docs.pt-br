---
title: Elemento <webRequestModules> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154537"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> Element (Network Settings) [Elemento webRequestModules> (configurações de rede)]
Especifica módulos a serem usados para solicitar informações de hosts de rede.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[adicionar](add-element-for-webrequestmodules-network-settings.md)|Adiciona um módulo de solicitação web personalizado ao aplicativo.|  
|[Claro](clear-element-for-webrequestmodules-network-settings.md)|Remove todos os módulos de solicitação da Web registrados do aplicativo.|  
|[remover](remove-element-for-webrequestmodules-network-settings.md)|Remove um módulo de solicitação web personalizado do aplicativo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
 O `webRequestModules` elemento registra descendentes <xref:System.Net.WebRequest> da classe para lidar com solicitações de informações para hosts de rede. Os módulos de <xref:System.Net.IWebRequestCreate> solicitação da Web devem implementar a interface.  
  
 O .NET Framework inclui módulos de solicitação `http://`da `https://`Web `file://`para URIs que começam com , e . Você pode substituir os módulos padrão apenas registrando um módulo personalizado no arquivo de configuração.  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra o módulo HTTP padrão. Você deve substituir os valores de Versão e PublicKeyToken pelos valores corretos para o módulo especificado.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Esquema de configurações de rede](index.md)
