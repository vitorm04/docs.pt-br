---
title: Hospedando enumerações
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
ms.openlocfilehash: 67a3617335db395b9d8f43c804c4eda65894723b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127000"
---
# <a name="hosting-enumerations"></a>Hospedando enumerações
Esta seção descreve as enumerações não gerenciadas que a API de hospedagem usa.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Enumeração CLSID_RESOLUTION_FLAGS](../../../../docs/framework/unmanaged-api/hosting/clsid-resolution-flags-enumeration.md)  
 Contém valores que indicam como o Common Language Runtime (CLR) deve resolver um `CLSID`.  
  
 [Enumeração COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 Especifica as estatísticas a serem registradas para uma coleta de lixo.  
  
 [Enumeração COR_GC_THREAD_STATS_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-types-enumeration.md)  
 Indica as estatísticas de coleta de lixo para um thread.  
  
 [Enumeração EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 Descreve as categorias de recursos que o host pode bloquear de ser executado em código parcialmente confiável.  
  
 [Enumeração EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)  
 Fornece sinalizadores que especificam o nível no qual aplicar ou modificar a política de assembly.  
  
 [Enumeração ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md)  
 Indica o tipo de identidade de um assembly.  
  
 [Enumeração EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 Descreve os eventos CLR para os quais o host pode registrar retornos de chamada.  
  
 [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 Descreve o conjunto de falhas para as quais um host pode definir ações de política.  
  
 [Enumeração EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 Descreve o conjunto de operações para as quais um host pode aplicar ações de política.  
  
 [Enumeração EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)  
 Descreve as opções disponíveis para gerenciar exceções que não são manipuladas no código do usuário.  
  
 [Enumeração EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 Descreve o contexto de segurança do thread em execução no momento.  
  
 [Enumeração ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 Contém valores que indicam quais itens incluir em um subconjunto personalizado de um despejo de heap ao relatar erros.  
  
 [Enumeração ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 Reservado para a extensão futura da estrutura da [estrutura CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) .  
  
 [Enumeração EHostApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/ehostapplicationpolicy-enumeration.md)  
 Indica como modificar um objeto de interface de [interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md) . Esta enumeração foi preterida.  
  
 [Enumeração EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)  
 Permite que o host especifique o tipo de redirecionamento que o CLR deve executar ao aplicar modificações de política de um assembly de origem a um assembly de destino.  
  
 [Enumeração EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)  
 Permite que o host forneça o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.  
  
 [Enumeração EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)  
 Contém valores que indicam a quantidade de memória física livre no computador.  
  
 [Enumeração EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)  
 Contém valores que indicam o impacto de uma falha quando uma alocação de memória específica é solicitada, mas não pode ser satisfeita.  
  
 [Enumeração EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 Descreve as ações de política que o host pode definir para operações descritas pela [Enumeração EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) e falhas descritas pela [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
 [Enumeração ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md)  
 Contém valores que definem a política para ler arquivos de banco de dados do programa (PDB).  
  
 [Enumeração ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md)  
 Contém valores que indicam o tipo de tarefa representado por uma [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou uma interface de [interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .  
  
 [Enumeração HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)  
 Contém valores que especificam o tipo de host que está iniciando um aplicativo.  
  
 [Enumeração MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)  
 Contém valores que especificam as características da memória que está sendo alocada.  
  
 [Enumeração METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md)  
 Descreve os possíveis sinalizadores retornados no parâmetro `pdwConfigFlags` do método [ICLRMetaHostPolicy:: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
 [Enumeração METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)  
 Fornece políticas de associação que são comuns à maioria dos hosts de tempo de execução.  
  
 [Enumeração RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
 Contém valores que indicam quais informações sobre o CLR devem ser retornadas.  
  
 [Enumeração StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)  
 Contém valores que indicam a causa subjacente de um evento de estouro de pilha.  
  
 [Enumeração STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
 Contém valores que indicam o comportamento de inicialização do CLR.  
  
 [Enumeração ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)  
 Contém valores que indicam o tipo de validação que deve ser executado em uma chamada para o [método Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md).  
  
 [Enumeração WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)  
 Indica a ação que um host deve executar se uma operação solicitada pelos blocos CLR.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Coclasses de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
