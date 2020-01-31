---
title: Método ICorProfilerCallback::ThreadCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 6514606290bf006443d7011c1a428bebb4cca0f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865823"
---
# <a name="icorprofilercallbackthreadcreated-method"></a>Método ICorProfilerCallback::ThreadCreated
Notifica o criador de perfil de que um thread foi criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadId`  
 no A ID do thread que foi criado.  
  
## <a name="remarks"></a>Comentários  
 O valor de `threadId` é imediatamente válido.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)
