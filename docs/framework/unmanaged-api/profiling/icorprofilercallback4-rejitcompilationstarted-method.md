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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8f2ada73686dfbe5629e21cfc6468becbd4ccc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597349"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>Método ICorProfilerCallback4::ReJITCompilationStarted
Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que o compilador JIT começou a recompilação.  
  
 `rejitId`  
 [in] A ID de recompilação da nova versão da função.  
  
 `fIsSafeToBlock`  
 [in] `true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução. Um valor de `true` não prejudicará o tempo de execução, mas podem afetar os resultados de criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) método chama para cada função devido à maneira o tempo de execução lida com construtores de classe. Por exemplo, o tempo de execução começa a recompilar um método de um, mas o construtor de classe para classe B precisa ser executado. Portanto, o tempo de execução recompila o construtor da classe B e o executa. Enquanto o construtor é executado, ele faz uma chamada ao método A, que faz com que o método A ser recompilado novamente. Nesse cenário, a primeira recompilação de um método de é interrompida. No entanto, ambas tentará recompilar A é relatada com eventos de recompilação JIT do método.  
  
 Os criadores de perfis devem dar suporte a sequência de retornos de chamada de recompilação JIT em casos em que dois threads simultaneamente fazendo retornos de chamada. Por exemplo, o thread A chama `ReJITCompilationStarted`; no entanto, antes de chamadas do thread A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), o thread B chama [ICorProfilerCallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do `ReJITCompilationStarted` retorno de chamada para o thread A. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não foi recebido pelo criador de perfil. No entanto, nesse caso, a ID de função é válida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [Método ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
