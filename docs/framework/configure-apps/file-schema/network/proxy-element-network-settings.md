---
title: Elemento <proxy> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154784"
---
# <a name="proxy-element-network-settings"></a>\<proxy> Element (Configurações de rede)
Define um servidor proxy.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>proxy**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`autoDetect`|Especifica se o proxy é detectado automaticamente. O valor padrão é `unspecified`.|  
|`bypassonlocal`|Especifica se o proxy é ignorado para os recursos locais. Os recursos locais incluem`http://localhost` `http://loopback`o `http://127.0.0.1`servidor local ( ou`http://webserver`) e um URI sem um período ( ). O valor padrão é `unspecified`.|  
|`proxyaddress`|Especifica o URI proxy a ser usado.|  
|`scriptLocation`|Especifica a localização do script de configuração. Não use `bypassonlocal` o atributo com este atributo. |  
|`usesystemdefault`|Especifica se deve usar as configurações de proxy do Internet Explorer. Se definido `true`como , atributos subseqüentes substituirão as configurações de proxy do Internet Explorer. O valor padrão é `unspecified`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Configura o servidor proxy Hypertext Transfer Protocol (HTTP).|  
  
## <a name="text-value"></a>Valor de texto  
  
## <a name="remarks"></a>Comentários  
 O `proxy` elemento define um servidor proxy para um aplicativo. Se esse elemento estiver ausente do arquivo de configuração, o .NET Framework usará as configurações de proxy no Internet Explorer.  
  
 O valor `proxyaddress` para o atributo deve ser um Indicador de Recurso Uniforme (URI) bem formado.  
  
 O `scriptLocation` atributo refere-se à detecção automática de scripts de configuração proxy. A <xref:System.Net.WebProxy> classe tentará localizar um script de configuração (geralmente chamado Wpad.dat) quando a opção **Usar script de configuração automática** for selecionada no Internet Explorer. Se `bypassonlocal` for definido como `scriptLocation` valor, é ignorado.
  
 Use `usesystemdefault` o atributo para aplicativos .NET Framework versão 1.1 que estão migrando para a versão 2.0.  
  
 Uma exceção é `proxyaddress` lançada se o atributo especificar um proxy padrão inválido. A <xref:System.Exception.InnerException%2A> propriedade na exceção deve ter mais informações sobre a causa raiz do erro.  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço proxy e ignora o proxy para acesso local.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
