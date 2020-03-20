---
title: Método ICorProfilerCallback4::ReJITCompilationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177089"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>Método ICorProfilerCallback4::ReJITCompilationStarted
Notifica o profiler de que o compilador just-in-time (JIT) começou a recompilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>parâmetros  
 `functionId`  
 [em] O ID da função que o compilador JIT começou a recompilar.  
  
 `rejitId`  
 [em] A iD de recompilação da nova versão da função.  
  
 `fIsSafeToBlock`  
 [em] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o retorno do segmento de chamada a partir deste retorno de chamada; `false` para indicar que o bloqueio não afetará o funcionamento do tempo de execução. Um valor `true` de não prejudica o tempo de execução, mas pode afetar os resultados de criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de `ReJITCompilationStarted` um par de chamadas do método [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução lida com construtores de classe. Por exemplo, o tempo de execução começa a recompilar o método A, mas o construtor de classe para a classe B precisa ser executado. Portanto, o tempo de execução recompila o construtor para a classe B e executa-o. Enquanto o construtor está em execução, ele faz uma chamada para o método A, que faz com que o método A seja recompilado novamente. Neste cenário, a primeira recompilação do método A é interrompida. No entanto, ambas as tentativas de recompilação do método A são relatadas com eventos de recompilação JIT.  
  
 Os profilers devem suportar a seqüência de recompilação de retornos de jit nos casos em que dois segmentos estão simultaneamente fazendo retornos de chamada. Por exemplo, chamadas `ReJITCompilationStarted`de thread A; no entanto, antes de thread A chama [ReJITCompilationFinished,](icorprofilercallback4-rejitcompilationfinished-method.md)o thread B chama [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) com o ID de função do retorno de chamada para o `ReJITCompilationStarted` segmento A. Pode parecer que o ID da função ainda não deve ser válido porque uma chamada para [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) ainda não havia sido recebida pelo profiler. No entanto, neste caso, o ID da função é válido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback4](icorprofilercallback4-interface.md)
- [Método JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)
- [Método ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)
