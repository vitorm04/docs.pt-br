---
title: Enumeração STARTUP_FLAGS
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f254582d96b310c247778818fc0d5daaae0d911c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737270"
---
# <a name="startupflags-enumeration"></a>Enumeração STARTUP_FLAGS
Contém valores que indicam o comportamento de inicialização do common language runtime (CLR). Por padrão, a coleta de lixo é não simultânea e somente a biblioteca de classe base é carregada para a área de domínio neutro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`STARTUP_CONCURRENT_GC`|Especifica que a coleta de lixo simultânea deve ser usada. Se o chamador solicita a compilação do servidor e coleta de lixo simultânea em um computador de processador único, a compilação de estação de trabalho e a coleta de lixo não simultânea são executadas em vez disso. **Observação:**  Não há suporte para a coleta de lixo simultânea em aplicativos que estão em execução no WOW64 x86 emulator em sistemas de 64 bits que implementam a arquitetura Intel Itanium (chamada anteriormente de IA-64). Para obter mais informações sobre como usar WOW64 em sistemas Windows de 64 bits, consulte [aplicativos de 32 bits em execução](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Especifica que a otimização do carregador deverá ocorrer.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Especifica que nenhum assembly é carregados como domínio neutro.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Especifica que todos os assemblies são carregados como domínio neutro.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Especifica que todos os assemblies de nome forte são carregados como domínio neutro.|  
|`STARTUP_LOADER_SAFEMODE`|Especifica que a política de versão CLR não será aplicada para a versão passada. A versão exata especificada do CLR será carregada. O shim não avalia a política para determinar a versão mais recente compatível.|  
|`STARTUP_LOADER_SETPREFERENCE`|Especifica que o tempo de execução preferencial será definido, mas na verdade não é iniciado.|  
|`STARTUP_SERVER_GC`|Especifica que a coleta de lixo do servidor será usada.|  
|`STARTUP_HOARD_GC_VM`|Especifica que a coleta de lixo manterá o endereço virtual usado.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Especifica que a combinação de uma interface de hospedagem não será permitida.|  
|`STARTUP_LEGACY_IMPERSONATION`|Especifica a representação não deve fluir entre pontos assíncronos por padrão.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Especifica que a pilha completa de threads não deve ser confirmada quando o thread for executado.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Especifica que as representações gerenciadas e as representações obtidas por meio da plataforma de invocação será flua entre pontos assíncronos. Por padrão, somente as representações gerenciadas fluirão entre pontos assíncronos.|  
|`STARTUP_TRIM_GC_COMMIT`|Especifica que a coleta de lixo usará menos espaço comprometido quando a memória do sistema é insuficiente. Ver `gcTrimCommitOnLowMemory` na [otimização para hospedagem na Web compartilhada](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Especifica que o rastreamento de eventos para Windows (ETW) é habilitado para eventos do common language runtime. Começando com o Windows Vista, o rastreamento de eventos está sempre habilitado, portanto, esse sinalizador não tem nenhum efeito. Ver [controlando o log do .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Especifica que o monitoramento de recursos de domínio do aplicativo está habilitado. Consulte a <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade e [ \<appDomainResourceMonitoring > elemento](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
