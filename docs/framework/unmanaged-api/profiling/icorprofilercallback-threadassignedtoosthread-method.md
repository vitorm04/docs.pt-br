---
title: "Método ICorProfilerCallback::ThreadAssignedToOSThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c70de2b53fd428361d5404aa406d2b2be67d0914
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a>Método ICorProfilerCallback::ThreadAssignedToOSThread
Notifica o criador de perfil que um thread gerenciado está sendo implementado usando um thread de sistema operacional específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `managedThreadId`  
 [in] O identificador do thread gerenciado.  
  
 `osThreadId`  
 [in] O identificador de thread do sistema operacional.  
  
## <a name="remarks"></a>Comentários  
 O `ThreadAssignedToOSThread` retorno de chamada existe para que o criador de perfil pode manter um mapeamento preciso em fibras de threads do sistema operacional para threads gerenciados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
