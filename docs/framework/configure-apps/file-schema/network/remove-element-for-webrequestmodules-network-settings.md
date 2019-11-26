---
title: Elemento <remove> para webRequestModules (Configurações de Rede)
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
ms.openlocfilehash: ca3a78a491c61b6e23dab0f96eebceb3157706ae
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089143"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a>\<remover > elemento para webRequestModules (configurações de rede)
Remove um módulo de solicitação da Web personalizado do aplicativo.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**remover >**
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Attribute**|**Descrição**|  
|-------------------|---------------------|  
|`prefix`|O prefixo de URI para solicitações tratadas por este módulo de solicitação da Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Especifica os módulos a serem usados para solicitar informações de hosts de rede.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `remove` remove o módulo de solicitação da Web registrado para o prefixo de URI especificado.  
  
 O valor para o atributo `prefix` deve ser os caracteres à esquerda de um URI válido, por exemplo, "`http`" ou "`http://www.contoso.com`".  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e registra um novo módulo de solicitação da Web personalizado para solicitações HTTP para `www.contoso.com`.
  
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

- <xref:System.Net.WebRequest>
- [Esquema de configurações de rede](index.md)
