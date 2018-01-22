---
title: "&lt;inicialização&gt; elemento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4299775cd23162839ab9846adc7d2c64cc18a404
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltstartupgt-element"></a>&lt;inicialização&gt; elemento
Especifica informações de inicialização de tempo de execução de linguagem comum.  
  
 \<configuration>  
\<startup>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|Atributo opcional.<br /><br /> Especifica se deseja habilitar o [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução ou usar o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] política de ativação.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy Attribute  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Habilitar [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução para o tempo de execução escolhido, que é associar as técnicas de ativação herdadas do tempo de execução (como o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) para o tempo de execução escolhido do arquivo de configuração em vez de limitá-los no CLR versão 2.0. Portanto, se você escolher a versão do CLR 4 ou posterior do arquivo de configuração, os assemblies de modo misto criados com versões anteriores do .NET Framework são carregados com a versão do CLR escolhida. Definir esse valor impede CLR versão 1.1 ou CLR versão 2.0 carregados no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo.|  
|`false`|Use a política de ativação padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior, que é permitir que o tempo de execução herdado técnicas de ativação para carregar o CLR versão 1.1 ou 2.0 no processo de. Definir esse valor impede que os assemblies de modo misto do carregamento para o .NET Framework 4 ou posterior, a menos que eles foram criados com o .NET Framework 4 ou posterior. Esse valor é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Os aplicativos criados com o tempo de execução versão 1.1 ou posterior devem usar o  **\<supportedRuntime >** elemento.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
 O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados com a versão 1.1 ou posterior do tempo de execução. Os aplicativos criados para oferecer suporte a apenas versão 1.0 do tempo de execução devem usar o  **\<requiredRuntime >** elemento.  
  
 O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignora o  **\<inicialização >** elemento e seus elementos filho.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>O atributo useLegacyV2RuntimeActivationPolicy  
 Esse atributo é útil se seu aplicativo usa caminhos de ativação herdadas, como o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja que esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo criado com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] , mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework. Nesses cenários, defina o atributo como `true`.  
  
> [!NOTE]
>  Definindo o atributo para `true` impede que o CLR versão 1.1 ou CLR versão 2.0 seja carregado no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo (consulte [execução lado a lado para interoperabilidade COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações de inicialização](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)  
 [Execução lado a lado para interoperabilidade COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [Execução lado a lado em processo](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
