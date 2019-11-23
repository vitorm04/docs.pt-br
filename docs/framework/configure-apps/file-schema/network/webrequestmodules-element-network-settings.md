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
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697470"
---
# <a name="webrequestmodules-element-network-settings"></a>\<elemento de > webRequestModules (configurações de rede)
Especifica os módulos a serem usados para solicitar informações de hosts de rede.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
 None.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|Adiciona um módulo de solicitação da Web personalizado ao aplicativo.|  
|[clear](clear-element-for-webrequestmodules-network-settings.md)|Remove todos os módulos de solicitação da Web registrados do aplicativo.|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|Remove um módulo de solicitação da Web personalizado do aplicativo.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `webRequestModules` registra os descendentes da classe <xref:System.Net.WebRequest> para tratar as solicitações de informações para os hosts de rede. Os módulos de solicitação da Web devem implementar a interface <xref:System.Net.IWebRequestCreate>.  
  
 O .NET Framework inclui módulos de solicitação da Web para URIs que começam com `http://`, `https://`e `file://`. Você pode substituir os módulos padrão somente registrando um módulo personalizado no arquivo de configuração.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir registra o módulo HTTP padrão. Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.  
  
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

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Esquema de configurações de rede](index.md)
