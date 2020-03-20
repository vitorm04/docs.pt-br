---
title: Elemento <module> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154823"
---
# <a name="module-element-network-settings"></a>\<módulo> Element (Configurações de rede)
Adiciona um novo módulo proxy ao aplicativo.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de proxy padrão**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<módulo>**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`type`|O nome do tipo totalmente <xref:System.Type.FullName%2A> qualificado (indicado pela propriedade) e <xref:System.Reflection.Assembly.FullName%2A> o nome de montagem (indicado pela propriedade), separados por uma comma, que implementa o proxy.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Configura o servidor proxy Hypertext Transfer Protocol (HTTP).|  
  
## <a name="remarks"></a>Comentários  
 O `module` elemento registra classes proxy <xref:System.Net.IWebProxy> que implementam a interface. Depois de registrar a `module` classe proxy, pode ser usado para solicitar informações através do proxy suportado.  
  
 O valor `type` para o atributo deve ser o nome da classe do módulo e o nome de sua Biblioteca de Link Dinâmico correspondente (DLL).  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra uma classe proxy personalizada.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
