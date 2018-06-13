---
title: Método ICorProfilerCallback8::DynamicMethodJITCompilationFinished
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454991"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>Método ICorProfilerCallback8::DynamicMethodJITCompilationFinished
[Com suporte nas versões posteriores e 4.7 do .NET Framework]  
  
Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória para o qual JIT compilação é iniciada.   

[in] `hrStatus`   
Um valor que indica se a compilação JIT foi bem-sucedida.

[in] `fIsSafeToBlock`   
`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; `false` para indicar que a bloqueio não afetará a operação do tempo de execução.  

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é disparado sempre que a compilação JIT de um método dinâmico foi concluída. Isso inclui várias stubs de IL e métodos LCG. Sua meta é fornecer informações suficientes para identificar o método compilado para usuários gravadores de criador de perfil.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos têm sem metadados.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
