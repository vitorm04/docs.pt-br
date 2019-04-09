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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efe3070b41b1d71e0cf533a7f9f211f4c6626726
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197848"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>Método ICorProfilerCallback3::ProfilerDetachSucceeded
Notifica o criador de perfil que o common language runtime (CLR) está prestes a descarregar a DLL do criador de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse retorno de chamada é ignorado.  
  
## <a name="remarks"></a>Comentários  
 O `ProfilerDetachSucceeded` retorno de chamada é emitido depois que todos os threads tenham saído código do criador de perfil. Quando este método é chamado, o criador de perfil deve executar qualquer tarefa de última hora que não é apropriada para seu destruidor, como notificar sua interface do usuário ou o componente de log. No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidos pelo CLR durante esse retorno de chamada (como o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*` interfaces).  
  
 O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação de desanexação for bem-sucedida.  
  
 Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto criador de perfil e descarrega a DLL do criador de perfil. Portanto, o criador de perfil não deve executar as ações que poderiam causar a execução ocorra dentro a DLL do criador de perfil depois que ele retorna desse retorno de chamada. Por exemplo, ele não deve criar threads ou registrar retornos de chamada do temporizador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Criação de perfil de interfaces](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
