---
title: Método ICorProfilerCallback3::ProfilerDetachSucceeded
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: b044c493649b73566a2e70db2e19977a6a7b877d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439452"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>Método ICorProfilerCallback3::ProfilerDetachSucceeded
Notifica o criador de perfil de que o Common Language Runtime (CLR) está prestes a descarregar a DLL do criador de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Valor retornado  
 O valor de retorno desse retorno de chamada é ignorado.  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada `ProfilerDetachSucceeded` é emitido depois que todos os threads saíram do código do criador de perfil. Quando esse método é chamado, o criador de perfil deve executar todas as tarefas de último minuto que não são apropriadas para seu destruidor, como notificar sua interface do usuário ou componente de log. No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidas pelo CLR durante esse retorno de chamada (como as interfaces [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*`).  
  
 O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação de desanexação foi bem-sucedida.  
  
 Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto Profiler e descarrega a DLL do criador de perfil. Portanto, o criador de perfil não deve executar nenhuma ação que faria com que a execução ocorresse dentro da DLL do criador de perfil depois de retornar desse retorno de chamada. Por exemplo, ele não deve criar threads ou registrar retornos de chamada do temporizador.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
