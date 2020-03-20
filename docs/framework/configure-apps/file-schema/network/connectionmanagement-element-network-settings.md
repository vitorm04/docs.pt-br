---
title: Elemento <connectionManagement> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154888"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement> Element (Network Settings) [Elemento connectionManagement> (configurações de rede)]
Especifica o número máximo de conexões a um host de rede.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>de gerenciamento de conexão**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[adicionar](add-element-for-connectionmanagement-network-settings.md)|Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexões.|  
|[Claro](clear-element-for-connectionmanagement-network-settings.md)|Limpa a lista de gerenciamento de conexões.|  
|[remover](remove-element-for-connectionmanagement-network-settings.md)|Remove um endereço IP ou nome DNS da lista de gerenciamento de conexão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
 O `connectionManagement` elemento define o número máximo de conexões a um servidor ou grupo de servidores.  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura um aplicativo para `www.contoso.com` usar quatro conexões para o servidor e duas conexões para todos os outros servidores.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Esquema de configurações de rede](index.md)
