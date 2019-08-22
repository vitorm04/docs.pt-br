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
ms.openlocfilehash: 3cf99a4dcf64b82846729d8663e398385b7a1086
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663459"
---
# <a name="runtime-element"></a>\<Elemento de > de tempo de execução

Fornece informações usadas pelo Common Language Runtime para configurar aplicativos.

\<> de configuração \
\<runtime>

## <a name="syntax"></a>Sintaxe

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Especifica se uma verificação de nome forte para assemblies confiáveis deve ser ignorada.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Especifica que o tempo de execução deve usar o comportamento de classificação herdado ao executar comparações de cadeia de caracteres.|
|[\<developmentMode>](developmentmode-element.md)|Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Especifica se o cache de falhas de associação, que é o comportamento padrão no .NET Framework versão 2,0, está desabilitado.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Especifica se a pilha de threads completa é confirmada quando um thread é iniciado.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Determina se os métodos de análise de data e hora usam um conjunto de regras ajustado para analisar sequências de datas que contêm somente um dia, mês, hora e designador AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).|
|[\<etwEnable>](etwenable-element.md)|Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.|
|[\<gcConcurrent>](gcconcurrent-element.md)|Especifica se o Common Language Runtime executa a coleta de lixo simultaneamente.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.|
|[\<gcServer>](gcserver-element.md)|Especifica se o Common Language Runtime executa a coleta de lixo do servidor.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Especifica se o tempo de execução usa a política de editor de CAS (Segurança de Acesso do Código).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Especifica se o tempo de execução permite que o código gerenciado detecte violações de acesso e outras exceções de estado corrompido.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Especifica se os assemblies de fontes remotas são carregados como confiança total.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Especifica se o tempo de execução usa a política de CAS (Segurança de Acesso do Código) herdada.|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Especifica se o tempo de execução usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|Especifica que o tempo de execução usará a interoperabilidade COM em vez de comunicação remota entre limites de domínio de aplicativo.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Otimiza o teste para assemblies satélites.|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no .NET Framework 4 ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Fornece informações de configuração para o cache de objeto na memória padrão.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|Especifica se o tempo de execução usa uma formatação herdada para valores de <xref:System.TimeSpan>.|
|[\<useLegacyJit>](uselegacyjit-element.md)|Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Especifica se o tempo de execução calcula códigos hash para sequências com base no domínio do aplicativo.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|As solicitações que o tempo de execução usa para explicitar os tamanhos das pilhas ao criar certos threads usados internamente, em vez do tamanho de pilha padrão.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|

## <a name="remarks"></a>Comentários

Os elementos filho na [ \<](runtime-element.md) seção de > de tempo de execução de um arquivo de configuração são usados pelo Common Language Runtime para configurar a execução de um aplicativo. Por exemplo, o [ \<elemento > gcServer](gcserver-element.md) determina se o coletor de lixo usa a coleta de lixo da estação de trabalho ou a coleta de lixo do servidor, o [ \<elemento UseRandomizedStringHashAlgorithm >](userandomizedstringhashalgorithm-element.md) Determina se o Common Language Runtime calcula códigos de hash para cadeia de caracteres em um domínio por aplicativo ou por aplicativo, e o `AppContextSwitchOverrides` elemento permite que os usuários de biblioteca aceitem ou recusem a funcionalidade alterada fornecida por uma biblioteca.

Os elementos na [ \<seção > de tempo de execução](runtime-element.md) são lidos automaticamente pelo Common Language Runtime na inicialização do aplicativo. Você também pode definir o arquivo de configuração para um domínio de aplicativo não padrão fornecendo seu nome à <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> Propriedade; suas configurações são lidas automaticamente quando o domínio do aplicativo é carregado. Você deve, raramente, ter a necessidade de ler diretamente as configurações na [ \<seção > de tempo de execução](runtime-element.md) no arquivo de configuração do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
