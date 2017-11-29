---
title: "Enumeração STARTUP_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: STARTUP_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: STARTUP_FLAGS
helpviewer_keywords: STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebfb45e6d568b4fa1db209264e02332df636474f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="startupflags-enumeration"></a>Enumeração STARTUP_FLAGS
Contém valores que indicam o comportamento de inicialização do common language runtime (CLR). Por padrão, a coleta de lixo é não simultânea e somente é carregar a biblioteca de classe base para a área de um domínio neutro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Especifica que a coleta de lixo simultânea deve ser usada. Se o chamador solicita a criação do servidor e a coleta de lixo simultânea em um computador com processador único, a criação de estação de trabalho e a coleta de lixo não simultânea são executados em vez disso. **Observação:** não há suporte para a coleta de lixo simultânea em aplicativos que estão executando o WOW64 x86 emulador em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamado de IA-64). Para obter mais informações sobre como usar o WOW64 em sistemas de 64 bits do Windows, consulte [aplicativos em execução de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Especifica que otimização carregador deve ocorrer.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Especifica que nenhum assembly é carregados como domínios neutros.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Especifica que todos os assemblies são carregados como domínios neutros.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Especifica que todos os assemblies de nomes fortes são carregados como domínios neutros.|  
|`STARTUP_LOADER_SAFEMODE`|Especifica que diretiva de versão do CLR não será aplicada para a versão passada. A versão exata especificada do CLR será carregada. A correção não avalia a política para determinar a versão compatível mais recente.|  
|`STARTUP_LOADER_SETPREFERENCE`|Especifica que o tempo de execução preferencial será definido, mas na verdade não iniciado.|  
|`STARTUP_SERVER_GC`|Especifica que a coleta de lixo do servidor será usada.|  
|`STARTUP_HOARD_GC_VM`|Especifica que a coleta de lixo manterá o endereço virtual usado.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Especifica que a combinação de uma interface de hospedagem não será permitida.|  
|`STARTUP_LEGACY_IMPERSONATION`|Especifica a representação não deve fluir pelos pontos assíncronos por padrão.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Especifica que a pilha do thread total não deve ser confirmada quando o thread é iniciado.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Especifica que a invocação de representações gerenciadas e representações obtidas por meio de plataforma será fluxo pelos pontos assíncronos. Por padrão, somente as representações gerenciadas fluirá pelos pontos assíncronos.|  
|`STARTUP_TRIM_GC_COMMIT`|Especifica que a coleta de lixo usará espaço menor confirmado quando a memória do sistema é insuficiente. Consulte `gcTrimCommitOnLowMemory` na [otimização da hospedagem Web compartilhada](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Especifica que o rastreamento de eventos para Windows (ETW) está habilitado para eventos de tempo de execução de linguagem comum. Começando com o Windows Vista, o rastreamento de eventos está sempre habilitado, portanto esse sinalizador não tem nenhum efeito. Consulte [controlando o log do .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Especifica que o monitoramento de recursos do domínio de aplicativo está habilitado. Consulte o <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade e [ \<appDomainResourceMonitoring > elemento](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
