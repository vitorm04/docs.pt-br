---
title: Elemento <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430463"
---
# <a name="runtime-element"></a>\<runtime> Element

Provides information used by the common language runtime to configure applications.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a>Sintaxe

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

The following sections describe child elements and parent elements.

### <a name="attributes"></a>Atributos

nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Instrui o runtime a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Especifica se uma verificação de nome forte para assemblies confiáveis deve ser ignorada.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Specifies that the runtime should use legacy sorting behavior when performing string comparisons.|
|[\<developmentMode>](developmentmode-element.md)|Especifica se o runtime pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Specifies whether the full thread stack is committed when a thread is started.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Especifica se o comportamento padrão, que é permitir que o host de runtime substitua as definições de configuração de um domínio de aplicativo, está desabilitado.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Determina se os métodos de análise de data e hora usam um conjunto de regras ajustado para analisar sequências de datas que contêm somente um dia, mês, hora e designador AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).|
|[\<etwEnable>](etwenable-element.md)|Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.|
|[\<gcConcurrent>](gcconcurrent-element.md)|Specifies whether the common language runtime runs garbage collection concurrently.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Defines the affinity between garbage collection heaps and individual processors.|
|[\<GCHeapCount>](gcheapcount-element.md)|Specifies the number of heaps/threads to use for server garbage collection.|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Specifies the threshold size that causes the garbage collector to put objects on the large object heap.|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Specifies whether or not to affinitize server garbage collection threads with CPUs.|
|[\<gcServer>](gcserver-element.md)|Especifica se o Common Language Runtime executa a coleta de lixo do servidor.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Especifica se o runtime usa a política de editor de CAS (Segurança de Acesso do Código).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Especifica se o runtime permite que o código gerenciado detecte violações de acesso e outras exceções de estado corrompido.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Especifica se os assemblies de fontes remotas são carregados como confiança total.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Especifica se o runtime usa a política de CAS (Segurança de Acesso do Código) herdada.|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Especifica se o runtime corrige automaticamente declarações de invocação de plataforma incorretas em runtime, às custas de transições mais lentas entre o código gerenciado e não gerenciado.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Especifica se o runtime usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|Especifica que o runtime usará a interoperabilidade COM em vez de comunicação remota entre limites de domínio de aplicativo.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Otimiza o teste para assemblies satélites.|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Fornece informações de configuração para o cache de objeto na memória padrão.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Especifica se o runtime distribui threads gerenciados entre todos os grupos de CPU.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|Especifica se o runtime usa uma formatação herdada para valores de <xref:System.TimeSpan>.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Especifica se o runtime calcula códigos hash para sequências com base no domínio do aplicativo.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|As solicitações que o runtime usa para explicitar os tamanhos das pilhas ao criar certos threads usados internamente, em vez do tamanho de pilha padrão.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|

## <a name="remarks"></a>Comentários

The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes. For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.

The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup. You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded. You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.

## <a name="see-also"></a>Consulte também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivos de configuração](../index.md)
