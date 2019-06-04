---
title: Elemento <startup>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 5b15c504a01a0ab8e17b8ad8811d9ed183609322
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456268"
---
# <a name="startup-element"></a>\<inicialização > elemento

Especifica informações de inicialização de tempo de execução de linguagem comum.

 \<configuration> \<startup>

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
|`useLegacyV2RuntimeActivationPolicy`|Atributo opcional.<br /><br /> Especifica se deseja habilitar o [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução ou para usar o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] política de ativação.|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>atributo useLegacyV2RuntimeActivationPolicy

|Valor|Descrição|
|-----------|-----------------|
|`true`|Habilitar [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução para o tempo de execução escolhido, é associar técnicas de ativação de tempo de execução herdado (como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) para o tempo de execução escolhido do arquivo de configuração em vez de limitação-los na versão 2.0 do CLR. Portanto, se a versão do CLR 4 ou posterior é escolhido do arquivo de configuração, assemblies de modo misto criados com versões anteriores do .NET Framework são carregados com a versão do CLR escolhida. Definir esse valor impede a versão 1.1 do CLR ou a versão 2.0 do CLR seja carregado para o mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo.|
|`false`|Use a política de ativação padrão para o .NET Framework 4 e posterior permitir a técnicas de ativação para carregar a versão 1.1 ou 2.0 do CLR no processo de execução herdado. Definir esse valor impede que os assemblies de modo misto do carregamento para o .NET Framework 4 ou posterior, a menos que eles foram criados com o .NET Framework 4 ou posterior. Esse valor é o padrão.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Aplicativos criados com o tempo de execução versão 1.1 ou posterior devem usar o  **\<supportedRuntime >** elemento.|
|[\<supportedRuntime>](supportedruntime-element.md)|Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|

## <a name="remarks"></a>Comentários

 O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados usando a versão 1.1 ou posterior do tempo de execução. Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o  **\<requiredRuntime >** elemento.

 O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignorará as  **\<inicialização >** elemento e seus elementos filho.

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>O atributo useLegacyV2RuntimeActivationPolicy

 Esse atributo é útil se seu aplicativo usa caminhos de ativação herdados, como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo criado com o .NET Framework 4, mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework. Nesses cenários, defina o atributo como `true`.

> [!NOTE]
> Definindo o atributo para `true` impede que o CLR versão 1.1 ou versão 2.0 do CLR seja carregado no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo (consulte [execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).

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

- [Esquema de configurações de inicialização](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [Execução lado a lado em processo](../../../deployment/in-process-side-by-side-execution.md)
