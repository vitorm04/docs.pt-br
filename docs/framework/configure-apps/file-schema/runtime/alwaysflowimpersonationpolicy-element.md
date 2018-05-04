---
title: '&lt;alwaysFlowImpersonationPolicy&gt; Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cc704bbf8631936dbbeb3539ea5ed0d8499f378
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysFlowImpersonationPolicy&gt; Element
Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.  
  
 \<configuration>  
\<runtime>  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Indica se a identidade do Windows flui pelos pontos assíncronos.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O identity não fluem pelos pontos assíncronos, a menos que a representação é realizada por meio do Windows gerenciado métodos como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Esse é o padrão.|  
|`true`|A identidade do Windows sempre flui pelos pontos assíncronos, independentemente de como a representação foi executada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões do .NET Framework 1.0 e 1.1, a identidade do Windows não fluem pelos pontos assíncronos. No .NET Framework versão 2.0, há um <xref:System.Threading.ExecutionContext> objeto que contém informações sobre o thread em execução no momento e ele ultrapassar assíncronos pontos em um domínio de aplicativo. O <xref:System.Security.Principal.WindowsIdentity> também fluxos como parte das informações que fluem pelos pontos assíncronos, desde que a representação foi obtida usando gerenciado métodos como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> e não por outros meios, como plataforma invocar métodos nativos. Esse elemento é usado para especificar que a identidade do Windows fluxo pelos pontos assíncronos, independentemente de como a representação foi alcançada.  
  
 Você pode alterar esse comportamento padrão de duas outras maneiras:  
  
1.  No código gerenciado em uma base por thread.  
  
     Você pode suprimir o fluxo em uma base por thread, modificando o <xref:System.Threading.ExecutionContext> e <xref:System.Security.SecurityContext> configurações usando o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> método.  
  
2.  Na chamada para a interface de hospedagem não gerenciada para carregar o common language runtime (CLR).  
  
     Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simple) é usada para carregar o CLR, você pode especificar um sinalizador especial na chamada para o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função. Para habilitar o modo de compatibilidade para todo o processo, defina o `flags` parâmetro [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) para `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Em um aplicativo do .NET Framework, esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.  
  
 Para um aplicativo ASP.NET, o fluxo de representação pode ser configurado no arquivo ASPNET encontrado na \<pasta Windows > \Microsoft.NET\Framework\vx.x.xxxx directory.  
  
 ASP.NET por padrão desabilita o fluxo de representação no arquivo ASPNET usando as seguintes configurações:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 No ASP.NET, se quiser permitir que o fluxo de representação em vez disso, você deve usar explicitamente as seguintes configurações:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar a identidade do Windows flui pelos pontos assíncronos, mesmo quando a representação é obtida através de meios diferentes métodos gerenciados.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<legacyImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
