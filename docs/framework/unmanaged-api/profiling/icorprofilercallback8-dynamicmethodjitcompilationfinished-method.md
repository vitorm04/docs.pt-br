---
title: 'ICorProfilerCallback8: método ynamicMethodJITCompilationFinished de:D'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136578"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8: método ynamicMethodJITCompilationFinished de:D
[Com suporte no .NET Framework 4,7 e versões posteriores]  
  
Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico for concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória para a qual a compilação JIT é iniciada.   

[in] `hrStatus`   
Um valor que indica se a compilação JIT foi bem-sucedida.

[in] `fIsSafeToBlock`   
`true` para indicar que o bloqueio pode fazer com que o tempo de execução aguarde até que o thread de chamada retorne deste retorno de chamada; `false` para indicar que o bloqueio não afetará a operação do tempo de execução.  

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é disparado sempre que a compilação JIT de um método dinâmico é concluída. Isso inclui vários stubs IL e métodos LCG. Seu objetivo é fornecer aos gravadores de criador de perfil informações suficientes para identificar o método compilado para os usuários.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver seus tokens de metadados, porque métodos dinâmicos não têm metadados.

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
