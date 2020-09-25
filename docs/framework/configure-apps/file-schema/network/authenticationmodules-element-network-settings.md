---
title: Elemento <authenticationModules> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 154a73a5fe3fa9e2b6b1c9e5c462b76bdc1ba640
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201740"
---
# <a name="authenticationmodules-element-network-settings"></a>Elemento \<authenticationModules> (Configurações de Rede)

Especifica os módulos usados para autenticar solicitações de rede.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Element**|**Descrição**|  
|-----------------|---------------------|  
|[add](add-element-for-authenticationmodules-network-settings.md)|Adiciona um módulo de autenticação ao aplicativo.|  
|[clear](clear-element-for-authenticationmodules-network-settings.md)|Limpa todos os módulos de autenticação do aplicativo.|  
|[remove](remove-element-for-authenticationmodules-network-settings.md)|Remove um módulo de autenticação do aplicativo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Element**|**Descrição**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  

 O `authenticationModule` elemento Especifica os módulos de autenticação que conduzem o processo de autenticação com um servidor. Um módulo de autenticação deve implementar a <xref:System.Net.IAuthenticationModule> interface.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  

 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir habilita um módulo de autenticação. Você deve substituir os valores de Version e PublicKeyToken pelos valores corretos para o módulo especificado.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Esquema de configurações de rede](index.md)
