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
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447710"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>Enumeração COR_PRF_SUSPEND_REASON
Indica o motivo pelo qual o tempo de execução é suspenso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|O tempo de execução é suspenso por um motivo não especificado.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|O tempo de execução é suspenso para atender a uma solicitação de coleta de lixo.<br /><br /> Os retornos de chamada relacionados à coleta de lixo ocorrem entre os retornos de chamada [ICorProfilerCallback:: RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) e [ICorProfilerCallback:: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) .|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|O tempo de execução é suspenso para que um `AppDomain` possa ser desligado.<br /><br /> Enquanto o tempo de execução é suspenso, o tempo de execução determinará quais threads estão no `AppDomain` que está sendo desligado e os definirá para anular quando eles forem retomados. Não há nenhum retorno de chamada específico do `AppDomain`durante essa suspensão.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|O tempo de execução é suspenso para que a densidade de código possa ocorrer.<br /><br /> O código está se esgotando massacre somente quando o compilador JIT (just-in-time) está ativo com a densidade de código habilitada. Os retornos de chamada de código que ocorrem entre os retornos de chamada `ICorProfilerCallback::RuntimeSuspendFinished` e `ICorProfilerCallback::RuntimeResumeStarted`. **Observação:**  O CLR JIT não tem funções no .NET Framework versão 2,0, portanto, esse valor não é usado em 2,0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|O tempo de execução é suspenso para que possa ser desligado. Ele deve suspender todos os threads para concluir a operação.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|O tempo de execução está suspenso para depuração em processo.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|O tempo de execução é suspenso para se preparar para uma coleta de lixo.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|O tempo de execução é suspenso para a recompilação JIT.|  
  
## <a name="remarks"></a>Comentários  
 Todos os threads de tempo de execução que estão em código não gerenciado têm permissão para continuar em execução até tentarem inserir novamente o tempo de execução, ponto em que eles também serão suspensos até que o tempo de execução seja retomado. Isso também se aplica a novos threads que entram no tempo de execução. Todos os threads dentro do tempo de execução serão suspensos imediatamente se estiverem no código passível de interrupção ou solicitados a suspender quando acessarem o código passível de interrupção.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
