---
title: Elemento <bypasslist> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154940"
---
# <a name="bypasslist-element-network-settings"></a>\<elemento> de bypasslist (configurações de rede)
Fornece um conjunto de expressões regulares que descrevem endereços que não usam um proxy.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de bypasslist**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[adicionar](add-element-for-bypasslist-network-settings.md)|Adiciona um endereço IP ou nome DNS à lista de desvio proxy.|  
|[Claro](clear-element-for-bypasslist-network-settings.md)|Limpa a lista de desvios.|  
|[remover](remove-element-for-bypasslist-network-settings.md)|Remove um endereço IP ou nome DNS da lista de desvio proxy.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Configura o servidor proxy Hypertext Transfer Protocol (HTTP).|  
  
## <a name="remarks"></a>Comentários  
 A lista de bypass contém expressões <xref:System.Net.WebRequest> regulares que descrevem URIs que as instâncias acessam diretamente em vez de através do servidor proxy.  
  
 Você deve ter cuidado ao especificar uma expressão regular para este elemento. A expressão regular\\"[a-z]+\\.contoso .com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com. Para combinar apenas um host no domínio contoso.com, use uma âncora ("$"): "[a-z]+\\.contoso\\.com$".  
  
 Para obter mais informações sobre expressões regulares, consulte . [.NET Framework Expressões Regulares](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona dois endereços à lista de desvios. O primeiro ignora o proxy para todos os servidores do domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192.168.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
