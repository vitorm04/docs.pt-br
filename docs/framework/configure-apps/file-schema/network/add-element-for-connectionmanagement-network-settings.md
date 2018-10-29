---
title: '&lt;Adicionar&gt; elemento para connectionManagement (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: a3b8de254c28aedc21df5baf54bd67527e35b7f9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201287"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a>&lt;Adicionar&gt; elemento para connectionManagement (configurações de rede)
Adiciona um endereço IP ou nome DNS à lista de gerenciamento de conexão.  
  
 \<configuration>  
\<system.net>  
\<connectionManagement >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`address`|Uma cadeia de caracteres que descreve um endereço IP ou nome DNS.|  
|`maxconnection`|O número máximo de conexões permitido para um servidor. Se não for fornecido, o padrão é 2.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Especifica o número máximo de conexões para um host de rede.|  
  
## <a name="remarks"></a>Comentários  
 O valor de `address` atributo deve ser um asterisco para indicar todas as conexões ou uma cadeia de caracteres do formulário `<schema>://<idn_hostname>[:<port>]`.  
  
 Se o URI passado para quaisquer APIs HTTP contém Unicode, o nome será convertido internamente usando <xref:System.Uri.DnsSafeHost%2A> que podem retornar uma cadeia de caracteres punicode (comportamento depende da configuração atual de IDN).  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir configura um aplicativo para usar quatro conexões com o servidor `www.contoso.com` e duas conexões com todos os outros servidores.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
