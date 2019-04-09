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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206584"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
[Com suporte no .NET Framework 4.7 e versões posteriores]  
  
Notifica o criador de perfil sempre que a compilação JIT de um método dinâmico foi concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parâmetros  
[in] `functionId`  
O identificador da função na memória para o qual JIT compilação é iniciada.   

[in] `hrStatus`   
Um valor que indica se a compilação JIT foi bem-sucedida.

[in] `fIsSafeToBlock`   
`true` para indicar que o bloqueio pode causar o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; `false` para indicar que a de bloqueio não afetará a operação de tempo de execução.  

## <a name="remarks"></a>Comentários  

Esse retorno de chamada é acionado sempre que a compilação JIT de um método dinâmico foi concluída. Isso inclui várias stubs de IL e os métodos LCG. Sua meta é fornecer os gravadores de criador de perfil com informações suficientes para identificar o método compilado para os usuários.

> [!NOTE]
> `functionId` valores não podem ser usados para resolver a seus tokens de metadados, como métodos dinâmicos não têm nenhum metadado.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Interface ICorProfilerCallback8](icorprofilercallback8-interface.md)
