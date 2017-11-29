---
title: "&lt;remover&gt; elemento authenticationModules (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eb8490241d4ec8a34a76aa6087c1f4d27d5cebb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a>&lt;remover&gt; elemento authenticationModules (configurações de rede)
Remove um módulo de autenticação do aplicativo.  
  
 \<configuration>  
\<System.NET >  
\<authenticationModules >  
\<Remover >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|**type**|O nome do módulo de autenticação a ser removido.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Especifica os módulos usados para autenticar solicitações de rede.|  
  
## <a name="remarks"></a>Comentários  
 O `remove` elemento remove os módulos de autenticação que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.  
  
 O valor para o `type` atributo deve ser um nome de classe válido.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir remove um módulo de autenticação.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
