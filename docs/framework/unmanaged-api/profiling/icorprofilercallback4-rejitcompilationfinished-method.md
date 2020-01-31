---
title: Método ICorProfilerCallback4::ReJITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: e010a49dabd3b44602136e70b4c5524a68bdd9e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865201"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>Método ICorProfilerCallback4::ReJITCompilationFinished
Notifica o criador de perfil de que o compilador JIT (just-in-time) concluiu a recompilação de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que foi recompilada.  
  
 `rejitId`  
 no A identidade da função de compilação JIT recompilada.  
  
 `hrStatus`  
 no Um valor que indica se a recompilação JIT foi bem-sucedida.  
  
 `fIsSafeToBlock`  
 [in] `true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.  
  
 Um valor de `true` não danifica o tempo de execução, mas pode afetar os resultados da criação de perfil.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback4](icorprofilercallback4-interface.md)
- [Método JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)
- [Método ReJITCompilationStarted](icorprofilercallback4-rejitcompilationstarted-method.md)
