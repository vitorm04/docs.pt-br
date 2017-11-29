---
title: '&lt;legacyImpersonationPolicy&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f6bed837ab7b0c6a4aebe6116c5ab28bbc62175
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlegacyimpersonationpolicygt-element"></a>&lt;legacyImpersonationPolicy&gt; elemento
Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.  
  
 \<configuration>  
\<tempo de execução >  
\<legacyImpersonationPolicy >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica que o <xref:System.Security.Principal.WindowsIdentity> não fluem pelos pontos assíncronos, independentemente do <xref:System.Threading.ExecutionContext> fluxo configurações no thread atual.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>fluxos pelos pontos assíncronos, dependendo do modo de <xref:System.Threading.ExecutionContext> fluxo configurações para o thread atual. Esse é o padrão.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>fluxo não pelos pontos assíncronos, independentemente do <xref:System.Threading.ExecutionContext> fluxo configurações no thread atual.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões do .NET Framework 1.0 e 1.1, o <xref:System.Security.Principal.WindowsIdentity> não flua por quaisquer pontos assíncronos definido pelo usuário. Iniciando com o .NET Framework versão 2.0, há um <xref:System.Threading.ExecutionContext> fluxos de objeto que contém informações sobre o thread em execução no momento e pelos pontos assíncronos dentro de um domínio de aplicativo. O <xref:System.Security.Principal.WindowsIdentity> está incluído neste contexto de execução e, portanto, também passa pelos pontos assíncronos, que significa que se existir um contexto de representação, ele irá fluir também.  
  
 Começando com o .NET Framework 2.0, você pode usar o `<legacyImpersonationPolicy>` elemento para especificar que <xref:System.Security.Principal.WindowsIdentity> não fluem pelos pontos assíncronos.  
  
> [!NOTE]
>  O common language runtime (CLR) está ciente das operações executadas usando somente código gerenciado, não de representação executada fora do código gerenciado, como por meio da plataforma chamar código não gerenciado ou por meio de chamadas diretas para funções do Win32 de representação. Somente gerenciado <xref:System.Security.Principal.WindowsIdentity> objetos possam fluir entre pontos assíncronos, a menos que o `alwaysFlowImpersonationPolicy` elemento foi definido como true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Definindo o `alwaysFlowImpersonationPolicy` elemento como true especifica que a identidade do Windows sempre flui pelos pontos assíncronos, independentemente de como a representação foi executada. Para obter mais informações sobre o fluxo não gerenciado a representação pelos pontos assíncronos, consulte [ \<alwaysFlowImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Você pode alterar esse comportamento padrão de duas outras maneiras:  
  
1.  No código gerenciado em uma base por thread.  
  
     Você pode suprimir o fluxo em uma base por thread, modificando o <xref:System.Threading.ExecutionContext> e <xref:System.Security.SecurityContext> configurações usando o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> método.  
  
2.  Na chamada para a interface de hospedagem não gerenciada para carregar o common language runtime (CLR).  
  
     Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simple) é usada para carregar o CLR, você pode especificar um sinalizador especial na chamada para o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função. Para habilitar o modo de compatibilidade para todo o processo, defina o `flags` parâmetro [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) para STARTUP_LEGACY_IMPERSONATION.  
  
 Para obter mais informações, consulte o [ \<alwaysFlowImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Em um aplicativo do .NET Framework, esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.  
  
 Para um aplicativo ASP.NET, o fluxo de representação pode ser configurado no arquivo ASPNET encontrado na \<pasta Windows > \Microsoft.NET\Framework\vx.x.xxxx directory.  
  
 ASP.NET por padrão desabilita o fluxo de representação no arquivo ASPNET usando as seguintes configurações:  
  
```  
configuration>  
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
 O exemplo a seguir mostra como especificar o comportamento herdado que não passa a identidade do Windows por meio de pontos assíncronos.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<alwaysFlowImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
