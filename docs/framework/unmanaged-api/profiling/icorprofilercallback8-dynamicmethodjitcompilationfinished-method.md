---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175103"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
[Suportado nas versões .NET Framework 4.7 e posteriores]  
  
Notifica o profiler sempre que a compilação JIT de um método dinâmico tiver sido concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>parâmetros  
[in] `functionId`  
O identificador da função in-memory para a qual a compilação JIT é iniciada.

[em] `hrStatus` Um valor que indica se a compilação JIT foi bem sucedida.

[em] `fIsSafeToBlock` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o retorno do segmento de chamada a partir deste retorno de 
 `true` chamada; `false` para indicar que o bloqueio não afetará o funcionamento do tempo de execução.  

## <a name="remarks"></a>Comentários  

Este retorno de chamada é acionado sempre que a compilação JIT de um método dinâmico tiver terminado. Isso inclui vários stubs IL e métodos LCG. Seu objetivo é fornecer aos escritores de profiler informações suficientes para identificar o método compilado aos usuários.

> [!NOTE]
> `functionId`os valores não podem ser usados para resolver seus tokens de metadados, porque os métodos dinâmicos não têm metadados.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Confira também

- [Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
