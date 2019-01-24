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
ms.openlocfilehash: 062229245e3ae209de0eda65d4be59e286f4da7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517741"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>Método ICorProfilerCallback8::DynamicMethodJITCompilationStarted
[Com suporte no .NET Framework 4.7 e versões posteriores]  
  
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
`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.  

[in] `pILHeader`    
Um ponteiro para o primeiro byte de cabeçalho de IL do método.   

[in] `cbILHeader`    
O número de bytes no cabeçalho de IL. 

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é acionado sempre que um método dinâmico é compilado em JIT. Isso inclui várias stubs de IL e os métodos LCG. Sua meta é fornecer os gravadores de criador de perfil com informações suficientes para identificar o método compilado para os usuários.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos não têm nenhum metadado.

O `pILHeader` ponteiro só é válido durante o retorno de chamada.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método DynamicMethodJITCompilationFinished](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
