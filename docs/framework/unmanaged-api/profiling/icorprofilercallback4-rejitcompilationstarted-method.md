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
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430200"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>Método ICorProfilerCallback4::ReJITCompilationStarted
Notifica o criador de perfil de que o compilador JIT (just-in-time) começou a recompilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que o compilador JIT começou a recompilar.  
  
 `rejitId`  
 no A ID de recompilação da nova versão da função.  
  
 `fIsSafeToBlock`  
 [in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução. Um valor de `true` não danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de chamadas de método `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) para cada função devido à maneira como o tempo de execução manipula construtores de classe. Por exemplo, o tempo de execução começa a recompilar o método A, mas o construtor de classe para a classe B precisa ser executado. Portanto, o tempo de execução recompila o construtor para a classe B e o executa. Enquanto o Construtor está em execução, ele faz uma chamada para o método A, o que faz com que o método A seja recompilado novamente. Nesse cenário, a primeira recompilação do método A é interrompida. No entanto, ambas as tentativas de recompilar o método A são relatadas com eventos de recompilação JIT.  
  
 Os profileres devem dar suporte à sequência de retornos de chamada de recompilação JIT em casos em que dois threads realizam simultaneamente retornos de chamada. Por exemplo, thread A chama `ReJITCompilationStarted`; no entanto, antes do thread A chamar [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B chama [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID da função do retorno de chamada `ReJITCompilationStarted` para o thread A. Pode parecer que a ID da função ainda não deve ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não tinha sido recebida pelo criador de perfil. No entanto, nesse caso, a ID da função é válida.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [Método ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
