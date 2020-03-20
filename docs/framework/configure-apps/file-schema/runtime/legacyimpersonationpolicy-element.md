---
title: Elemento <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154096"
---
# <a name="legacyimpersonationpolicy-element"></a>\<elemento de> de representação de representação legado
Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legadoRepresentaçãoPolítica>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica que <xref:System.Security.Principal.WindowsIdentity> o fluxo não flui através de pontos <xref:System.Threading.ExecutionContext> assíncronos, independentemente das configurações de fluxo no segmento atual.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>flui através de pontos assíncronos, dependendo das <xref:System.Threading.ExecutionContext> configurações de fluxo para o segmento atual. Esse é o padrão.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>não flui através de pontos assíncronos, independentemente das <xref:System.Threading.ExecutionContext> configurações de fluxo no segmento atual.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões .NET Framework 1.0 <xref:System.Security.Principal.WindowsIdentity> e 1.1, o fluxo não flui em nenhum ponto assíncrono definido pelo usuário. Começando com a versão 2.0 do <xref:System.Threading.ExecutionContext> .NET Framework, há um objeto que contém informações sobre o segmento em execução atualmente, e ele flui através de pontos assíncronos dentro de um domínio de aplicativo. O <xref:System.Security.Principal.WindowsIdentity> está incluído neste contexto de execução e, portanto, também flui através dos pontos assíncronos, o que significa que se existe um contexto de personificação, ele fluirá também.  
  
 Começando com o .NET Framework 2.0, você pode usar o `<legacyImpersonationPolicy>` elemento para especificar que <xref:System.Security.Principal.WindowsIdentity> não flui entre pontos assíncronos.  
  
> [!NOTE]
> O tempo de execução da linguagem comum (CLR) está ciente das operações de personificação realizadas usando apenas código gerenciado, não de personificação realizada fora do código gerenciado, como através da invocação da plataforma para código não gerenciado ou através de chamadas diretas para funções Win32. Somente objetos gerenciados <xref:System.Security.Principal.WindowsIdentity> podem fluir através de `alwaysFlowImpersonationPolicy` pontos assíncronos, a menos que o elemento tenha sido definido como verdadeiro ().`<alwaysFlowImpersonationPolicy enabled="true"/>` Definir `alwaysFlowImpersonationPolicy` o elemento como verdadeiro especifica que a identidade do Windows sempre flui através de pontos assíncronos, independentemente de como a personificação foi realizada. Para obter mais informações sobre a representação não gerenciada em pontos assíncronos, consulte [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
 Você pode alterar esse comportamento padrão de duas outras maneiras:  
  
1. Em código gerenciado por segmento.  
  
     Você pode suprimir o fluxo por segmento modificando <xref:System.Threading.ExecutionContext> as configurações <xref:System.Security.SecurityContext> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> usando <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>método ou método .  
  
2. Na chamada para a interface de hospedagem não gerenciada para carregar o tempo de execução do idioma comum (CLR).  
  
     Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Para habilitar o modo de compatibilidade `flags` para todo o processo, defina o parâmetro para [corBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) para STARTUP_LEGACY_IMPERSONATION.  
  
 Para obter mais informações, consulte o [ \<elemento de> alwaysFlowImpersonationPolicy](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Em um aplicativo .NET Framework, esse elemento só pode ser usado no arquivo de configuração do aplicativo.  
  
 Para um aplicativo ASP.NET, o fluxo de personificação pode ser configurado no \<diretório aspnet.config encontrado no diretório Windows Folder>\Microsoft.NET\Framework\vx.xxxx.  
  
 ASP.NET por padrão desativa o fluxo de personificação no arquivo aspnet.config usando as seguintes configurações:  
  
``` xml
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
 O exemplo a seguir mostra como especificar o comportamento legado que não flui a identidade do Windows em pontos assíncronos.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md)
