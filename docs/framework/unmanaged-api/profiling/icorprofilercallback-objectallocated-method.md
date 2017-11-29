---
title: "Método ICorProfilerCallback::ObjectAllocated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectAllocated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a7e67e6085db4b73ca39688935767072ceadb68e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackobjectallocated-method"></a>Método ICorProfilerCallback::ObjectAllocated
Notifica o criador de perfil que foi alocada para um objeto de memória no heap.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `objectId`  
 [in] A ID do objeto para o qual a memória foi alocada.  
  
 `classId`  
 [in] A ID da classe da qual o objeto é uma instância.  
  
## <a name="remarks"></a>Comentários  
 O `ObjectedAllocated` método não é chamado para alocações da pilha ou memória não gerenciada. O `classId` parâmetro pode se referir a uma classe em código gerenciado que ainda não foi carregada. O criador de perfil receberá um retorno de chamada de carregamento de classe para a classe imediatamente após o `ObjectAllocated` retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [Método ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
