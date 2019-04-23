---
title: Método ICorProfilerCallback::ThreadAssignedToOSThread
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefcd4436a28fdf52cbe55da5d4bb7eea4449463
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158451"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a>Método ICorProfilerCallback::ThreadAssignedToOSThread
Notifica o criador de perfil que um thread gerenciado está sendo implementado usando um thread de sistema operacional específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `managedThreadId`  
 [in] O identificador do thread gerenciado.  
  
 `osThreadId`  
 [in] O identificador do thread do sistema operacional.  
  
## <a name="remarks"></a>Comentários  
 O `ThreadAssignedToOSThread` retorno de chamada existe para que o criador de perfil pode manter um mapeamento preciso em fibras de threads do sistema operacional para threads gerenciados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
