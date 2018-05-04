---
title: '&lt;tempo de execução&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fb050a8d73c42094caf83ba00c5dfc2e4d472723
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltruntimegt-element"></a>&lt;tempo de execução&gt; elemento
Fornece informações usadas pelo common language runtime para configurar os aplicativos.  
  
 \<configuration>  
\<runtime>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos filho e pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Define uma ou mais opções usadas pela classe <xref:System.AppContext> para fornecer um mecanismo de recusa de uma nova funcionalidade.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Instrui o tempo de execução a coletar estatísticas sobre todos os domínios de aplicativos no processo durante toda a vida do processo.|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Especifica se uma verificação de nome forte para assemblies confiáveis deve ser ignorada.|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Especifica que o tempo de execução deve usar o comportamento de classificação herdado ao executar comparações de cadeia de caracteres.|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Especifica se o cache de falhas de associação, que é o comportamento padrão do .NET Framework versão 2.0, está desabilitada.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Especifica se a pilha do thread completo é confirmada quando um thread é iniciado.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Determina se os métodos de análise de data e hora usam um conjunto de regras ajustado para analisar sequências de datas que contêm somente um dia, mês, hora e designador AM/PM.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Especifica se o common language runtime executa a coleta de lixo simultaneamente.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Especifica se o Common Language Runtime executa a coleta de lixo do servidor.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Especifica se o tempo de execução usa a política de editor de CAS (Segurança de Acesso do Código).|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Especifica se o tempo de execução permite que o código gerenciado detecte violações de acesso e outras exceções de estado corrompido.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Especifica se os assemblies de fontes remotas são carregados como confiança total.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Especifica se o tempo de execução usa a política de CAS (Segurança de Acesso do Código) herdada.|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Especifica se o tempo de execução usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Especifica que o tempo de execução usará a interoperabilidade COM em vez de comunicação remota entre limites de domínio de aplicativo.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Otimiza o teste para assemblies satélites.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Fornece informações de configuração para o cache de objeto na memória padrão.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Especifica se o tempo de execução usa uma formatação herdada para valores de <xref:System.TimeSpan>.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Determina se o Common Language Runtime usa o compilador JIT de 64 bits herdado para uma compilação just-in-time.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Especifica se o tempo de execução calcula códigos hash para sequências com base no domínio do aplicativo.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|As solicitações que o tempo de execução usa para explicitar os tamanhos das pilhas ao criar certos threads usados internamente, em vez do tamanho de pilha padrão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
 Elementos filhos a [ \<tempo de execução >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) seção de um arquivo de configuração são usadas pelo tempo de execução de linguagem comum para configurar como um aplicativo é executado. Por exemplo, o [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento determina se o coletor de lixo usa coleta de lixo de estação de trabalho ou a coleta de lixo do servidor, o [ \< UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) elemento determina se o common language runtime calcula os códigos de hash para a cadeia de caracteres por aplicativo ou um domínio de aplicativo e o `AppContextSwitchOverrides` elemento permite que os usuários da biblioteca para aceitar ou recusar alterada funcionalidade fornecida por uma biblioteca.  
  
 Os elementos de [ \<tempo de execução >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) seção são lidas automaticamente pelo common language runtime na inicialização do aplicativo. Você também pode definir o arquivo de configuração para um domínio de aplicativo não padrão, fornecendo seu nome para o <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> propriedade; suas configurações são lidas automaticamente quando o domínio de aplicativo é carregado. Raramente, ou nunca, que precisa ler diretamente as configurações de [ \<tempo de execução >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) seção no arquivo de configuração do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
