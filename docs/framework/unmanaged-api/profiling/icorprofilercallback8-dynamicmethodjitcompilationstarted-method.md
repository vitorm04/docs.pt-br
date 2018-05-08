---
title: Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted
[Com suporte nas versões posteriores e 4.7 do .NET Framework]  
  
Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi iniciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória para o qual JIT compilação é iniciada.   

[in] `fIsSafeToBlock`   
`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; `false` para indicar que a bloqueio não afetará a operação do tempo de execução.  

[in] `pILHeader`    
Um ponteiro para o primeiro byte de cabeçalho de IL do método.   

[in] `cbILHeader`    
O número de bytes no cabeçalho de IL. 

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é acionado sempre que um método dinâmico é a compilação JIT. Isso inclui várias stubs de IL e métodos LCG. Sua meta é fornecer informações suficientes para identificar o método compilado para usuários gravadores de criador de perfil.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos têm sem metadados.

O `pILHeader` ponteiro só é válido durante o retorno de chamada.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
