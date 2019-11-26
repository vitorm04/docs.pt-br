---
title: Elemento <add> para bypasslist (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 1db0ba3b0a213de1175e6e0cee347753d2a413b7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699605"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<adicionar o elemento > para BypassList (configurações de rede)
Adiciona um endereço IP ou nome DNS à lista de bypass de proxy.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultproxy >** ](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BypassList >** ](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
  
|**Attribute**|**Descrição**|  
|-------------------|---------------------|  
|**address**|Uma expressão regular que descreve um endereço IP ou nome DNS.|  
  
### <a name="child-elements"></a>Elementos filho  
 None.  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `add` insere expressões regulares descrevendo endereços IP ou nomes de servidor DNS na lista de endereços que ignoram um servidor proxy.  
  
 O valor do atributo `address` deve ser uma expressão regular que descreve um conjunto de endereços IP ou nomes de host.  
  
 Tome cuidado ao especificar uma expressão regular para este elemento. A expressão regular "[a-z] +\\. contoso\\. com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com. Para corresponder apenas a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\. contoso\\. com $".  
  
 Para obter mais informações sobre expressões regulares, consulte. [.NET Framework expressões regulares](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir adiciona dois endereços à lista de bypass. O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujo endereço IP começa com 192,168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
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
