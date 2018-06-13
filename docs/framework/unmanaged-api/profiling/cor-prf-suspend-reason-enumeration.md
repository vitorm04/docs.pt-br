---
title: Enumeração COR_PRF_SUSPEND_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f4382c7fa85008de9e67ad21c467402bae4ac90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451276"
---
# <a name="corprfsuspendreason-enumeration"></a>Enumeração COR_PRF_SUSPEND_REASON
Indica o motivo que o tempo de execução é suspensa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|O tempo de execução foi suspenso por um motivo não especificado.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|O tempo de execução é suspensa para atender uma solicitação de coleta de lixo.<br /><br /> Os retornos de chamada relacionadas à coleção lixo ocorrem entre o [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e [: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) retornos de chamada.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|O tempo de execução é suspensa para que um `AppDomain` pode ser desligado.<br /><br /> Durante o tempo de execução é suspensa, o tempo de execução determinará quais segmentos no `AppDomain` que é que está sendo desligado e defini-las para anular quando eles retomam. Não há nenhum `AppDomain`-retornos de chamada específicos durante esta suspensão.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|O tempo de execução é suspensa para que o código apresentando pode ocorrer.<br /><br /> Expondo código tem lugar somente quando compilador just-in-time (JIT) está ativo com código apresentando habilitado. Código de densidade de retornos de chamada ocorrerem entre a `ICorProfilerCallback::RuntimeSuspendFinished` e `ICorProfilerCallback::RuntimeResumeStarted` retornos de chamada. **Observação:** CLR JIT não com densidade funções do .NET Framework versão 2.0, para que esse valor não é usado no 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|O tempo de execução é suspensa para que seja desligado. Ele deve suspender todos os threads para concluir a operação.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|O tempo de execução é suspensa para depuração em andamento.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|O tempo de execução é suspensa para se preparar para uma coleta de lixo.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|O tempo de execução é suspensa para recompilação de JIT.|  
  
## <a name="remarks"></a>Comentários  
 Todos os threads de tempo de execução que estão em código não gerenciado tem permissão para continuar a execução até que eles tentam inserir novamente o tempo de execução, no ponto em que eles serão também suspensos até que o tempo de execução é retomada. Isso também se aplica a novos segmentos que insira o tempo de execução. Todos os threads no tempo de execução são suspensos imediatamente se eles estiverem em código passível de interrupção ou solicitados quando atingem código passível de suspensão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
