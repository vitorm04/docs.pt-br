---
title: "Método ICorProfilerCallback::ClassUnloadFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 920fa36edcc49c12f8f73644cc4e6551a0e954ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>Método ICorProfilerCallback::ClassUnloadFinished
Notifica o criador de perfil que uma classe terminou de descarregamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] Identifica a classe que foi descarregada.  
  
 `hrStatus`  
 [in] Um HRESULT que indica se a classe foi descarregada com êxito.  
  
## <a name="remarks"></a>Comentários  
 Algumas partes do descarregamento de classe podem continuar após o `ClassUnloadFinished` retorno de chamada. Uma falha de HRESULT em `hrStatus` indica uma falha. No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregar a classe foi bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ClassUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
