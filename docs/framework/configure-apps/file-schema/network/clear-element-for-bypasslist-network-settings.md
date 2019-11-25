---
title: Elemento <clear> para bypasslist (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 2ad6b16370f600299439d2e810dfefa1b5fa3c06
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087540"
---
# <a name="clear-element-for-bypasslist-network-settings"></a>\<limpar > elemento para BypassList (configurações de rede)
Limpa a lista de bypass de proxy.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[BypassList](bypasslist-element-network-settings.md)|Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `clear` limpa todas as entradas da lista de bypass.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir limpa a lista de bypass e, em seguida, adiciona dois endereços à lista de bypass. O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192,168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
