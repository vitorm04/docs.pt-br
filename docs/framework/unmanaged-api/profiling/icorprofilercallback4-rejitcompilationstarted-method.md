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
ms.openlocfilehash: d3e21d42340378c576bfc65750fba26a257b82cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457740"
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
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que o compilador JIT começou a recompilação.  
  
 `rejitId`  
 [in] A ID de recompilação da nova versão da função.  
  
 `fIsSafeToBlock`  
 [in] `true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; `false` para indicar que a bloqueio não afetará a operação do tempo de execução. Um valor de `true` não prejudicar o tempo de execução, mas podem afetar os resultados da criação de perfil.  
  
## <a name="remarks"></a>Comentários  
 É possível receber mais de um par de `ReJITCompilationStarted` e [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) método chama para cada função devido a maneira como o tempo de execução construtores de classe de identificadores. Por exemplo, o tempo de execução inicia a recompilação de um método de, mas o construtor de classe para classe B deve ser executado. Portanto, o tempo de execução recompila o construtor de classe B e o executa. Durante a execução, o construtor faz uma chamada ao método A, que faz com que o método A ser recompilado novamente. Nesse cenário, a recompilação de primeiro do método um é interrompida. No entanto, ambos tenta recompilar o método A é relatada com eventos de recompilação de JIT.  
  
 Criadores de perfil devem dar suporte a sequência de retornos de chamada de recompilação de JIT em casos onde dois threads simultaneamente fazem retornos de chamada. Por exemplo, um thread de chamadas `ReJITCompilationStarted`; no entanto, antes de chamadas do thread A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), chamadas de thread B [: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) com a ID de função do `ReJITCompilationStarted` retorno de chamada do thread A. Pode parecer que a ID de função não deve ainda ser válida porque uma chamada para [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) ainda não foi recebido pelo criador de perfil. No entanto, nesse caso, a ID de função é válida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [Método JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [Método ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
