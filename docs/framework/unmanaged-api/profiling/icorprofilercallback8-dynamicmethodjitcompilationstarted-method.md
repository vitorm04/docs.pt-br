---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177040"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
[Suportado nas versões .NET Framework 4.7 e posteriores]  
  
Notifica o profiler sempre que a compilação JIT de um método dinâmico foi iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>parâmetros  
[in] `functionId`  
O identificador da função in-memory para a qual a compilação JIT é iniciada.

[em] `fIsSafeToBlock` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde o retorno do segmento de chamada a partir deste retorno de 
 `true` chamada; `false` para indicar que o bloqueio não afetará o funcionamento do tempo de execução.  

[em] `pILHeader` Um ponteiro para o primeiro byte do cabeçalho IL do método.

[em] `cbILHeader` O número de bytes no cabeçalho IL.

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é acionado sempre que um método dinâmico é compilado pelo JIT. Isso inclui vários stubs IL e métodos LCG. Seu objetivo é fornecer aos escritores de profiler informações suficientes para identificar o método compilado aos usuários.

> [!NOTE]
> `functionId`os valores não podem ser usados para resolver seus tokens de metadados, porque os métodos dinâmicos não têm metadados.

O `pILHeader` ponteiro só é válido durante o retorno de chamada.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Confira também

- [Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
