---
title: Elemento <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154477"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Element
Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowPersonionPolicy>**\  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Indica se a identidade do Windows flui através de pontos assíncronos.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|A identidade do Windows não flui através de pontos assíncronos, a <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>menos que a personificação seja realizada através de métodos gerenciados como . Esse é o padrão.|  
|`true`|A identidade do Windows sempre flui através de pontos assíncronos, independentemente de como a representação foi realizada.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões .NET Framework 1.0 e 1.1, a identidade do Windows não flui através de pontos assíncronos. Na versão 2.0 do .NET <xref:System.Threading.ExecutionContext> Framework, há um objeto que contém informações sobre o segmento em execução atualmente e flui-os através de pontos assíncronos dentro de um domínio de aplicativo. O <xref:System.Security.Principal.WindowsIdentity> fluxo também flui como parte das informações que fluem através dos pontos assíncronos, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> desde que a personificação tenha sido alcançada usando métodos gerenciados como e não por outros meios, como a invocação da plataforma para métodos nativos. Este elemento é usado para especificar que a identidade do Windows flui através de pontos assíncronos, independentemente de como a personificação foi alcançada.  
  
 Você pode alterar esse comportamento padrão de duas outras maneiras:  
  
1. Em código gerenciado por segmento.  
  
     Você pode suprimir o fluxo por segmento modificando <xref:System.Threading.ExecutionContext> as configurações <xref:System.Security.SecurityContext> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>usando <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>método , ou método.  
  
2. Na chamada para a interface de hospedagem não gerenciada para carregar o tempo de execução do idioma comum (CLR).  
  
     Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Para habilitar o modo de compatibilidade `flags` para todo o processo, defina `STARTUP_ALWAYSFLOW_IMPERSONATION`o parâmetro para [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) para .  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Em um aplicativo .NET Framework, esse elemento só pode ser usado no arquivo de configuração do aplicativo.  
  
 Para um aplicativo ASP.NET, o fluxo de personificação pode ser configurado no \<diretório aspnet.config encontrado no diretório Windows Folder>\Microsoft.NET\Framework\vx.xxxx.  
  
 ASP.NET por padrão desativa o fluxo de personificação no arquivo aspnet.config usando as seguintes configurações:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Em ASP.NET, se você quiser permitir o fluxo de personificação, em vez disso, você deve usar explicitamente as seguintes configurações:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que a identidade do Windows flui através de pontos assíncronos, mesmo quando a personificação é alcançada através de meios diferentes dos métodos gerenciados.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [\<elemento de> de representação de representação legado](legacyimpersonationpolicy-element.md)
