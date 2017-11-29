---
title: "Método ICorProfilerCallback3::ProfilerDetachSucceeded"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4413e5c475bce6d6f2eea1f7a968c946237f47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>Método ICorProfilerCallback3::ProfilerDetachSucceeded
Notifica o criador de perfil que o common language runtime (CLR) está prestes a Descarregue o DLL do criador de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse retorno de chamada é ignorado.  
  
## <a name="remarks"></a>Comentários  
 O `ProfilerDetachSucceeded` retorno de chamada for emitido após todos os threads abandonaram o código do criador de perfil. Quando este método é chamado, o criador de perfil deve executar as tarefas de última hora que não são apropriadas para seu destruidor, como notificar sua interface do usuário ou o componente de log. No entanto, o criador de perfil não deve chamar funções em interfaces que são fornecidas pelo CLR durante esse retorno de chamada (como o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*` interfaces).  
  
 O CLR cria uma entrada no log de eventos de aplicativo do Windows para indicar que a operação desanexar é bem-sucedida.  
  
 Depois que o criador de perfil retorna desse retorno de chamada, o CLR libera o objeto do criador de perfil e descarrega o DLL do criador de perfil. Portanto, o criador de perfil não deve executar qualquer ação que cause a execução para ocorrer dentro de DLL do criador de perfil depois de retornar desse retorno de chamada. Por exemplo, ele não deve criar threads ou registrar retornos de chamada timer.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
