---
title: 'ICorProfilerCallback8: método ynamicMethodJITCompilationStarted de:D'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136457"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8: método ynamicMethodJITCompilationStarted de:D
[Com suporte no .NET Framework 4,7 e versões posteriores]  
  
Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória para a qual a compilação JIT é iniciada.   

[in] `fIsSafeToBlock`   
`true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.  

[in] `pILHeader`    
Um ponteiro para o primeiro byte do cabeçalho IL do método.   

[in] `cbILHeader`    
O número de bytes no cabeçalho IL. 

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é disparado sempre que um método dinâmico é compilado por JIT. Isso inclui vários stubs IL e métodos LCG. Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver seus tokens de metadados, porque métodos dinâmicos não têm metadados.

O ponteiro de `pILHeader` só é válido durante o retorno de chamada.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
