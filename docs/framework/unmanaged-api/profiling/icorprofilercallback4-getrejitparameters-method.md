---
title: Método ICorProfilerCallback4::GetReJITParameters
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865305"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>Método ICorProfilerCallback4::GetReJITParameters
Permite que o criador de perfil de código defina sinalizadores de geração de código alternativos para um novo corpo de método recompilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleID`  
 no O módulo que contém o método para o qual o CLR precisa de parâmetros de recompilação JIT.  
  
 `methodId`  
 no O `MethodDef` do método para o qual o CLR precisa de parâmetros de recompilação JIT.  
  
 `pFunctionControl`  
 no Um ponteiro para uma interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) que o criador de perfil pode usar para fornecer informações de recompilação JIT para o método que está sendo recompilado.  
  
## <a name="remarks"></a>Comentários  
 O CLR emite um retorno de chamada `GetReJITParameters` para que o criador de perfil possa especificar os parâmetros para a recompilação de um determinado método. O retorno de chamada `GetReJITParameters` é emitido apenas uma vez por função; os parâmetros fornecidos pelo criador de perfil se aplicam a todas as instâncias dessa função.  
  
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
