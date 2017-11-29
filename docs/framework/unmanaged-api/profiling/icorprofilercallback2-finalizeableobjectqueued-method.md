---
title: "Método ICorProfilerCallback2::FinalizeableObjectQueued"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.FinalizeableObjectQueued
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ff90fd6df337f7b92a73b43b6abc488da7ed6b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a>Método ICorProfilerCallback2::FinalizeableObjectQueued
Notifica o criador de perfil de código que um objeto com um finalizador foi enfileirado para o thread do finalizador para execução do seu `Finalize` método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `finalizerFlags`  
 [in] Um valor de [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeração que descreve aspectos do finalizador.  
  
 `objectID`  
 [in] A ID do objeto que foi colocado em fila.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
