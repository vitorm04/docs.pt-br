---
title: "Método ICorProfilerCallback::RuntimeSuspendAborted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d1c181a471763ea0220c081d64af915ca6be149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>Método ICorProfilerCallback::RuntimeSuspendAborted
Notifica o criador de perfil que o tempo de execução foi anulada a suspensão de tempo de execução estava ocorrendo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Comentários  
 A suspensão de tempo de execução pode ser anulada se dois threads simultaneamente tentarem suspender o tempo de execução.  
  
 Ambos o [Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) retorno de chamada ou `RuntimeSuspendAborted` retorno de chamada será feita na seguinte único thread um [Runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) retorno de chamada.  
  
 O `RuntimeSuspendAborted` tem garantia de retorno de chamada ocorrer no mesmo thread, como o `RuntimeSuspendStarted` retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
