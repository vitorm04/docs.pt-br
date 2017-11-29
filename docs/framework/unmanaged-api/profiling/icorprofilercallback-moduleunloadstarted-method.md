---
title: "Método ICorProfilerCallback::ModuleUnloadStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069e47ad3d1dd9459b7344b1af1a2ad6d32305ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>Método ICorProfilerCallback::ModuleUnloadStarted
Notifica o criador de perfil que um módulo está sendo descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo que está sendo descarregado.  
  
## <a name="remarks"></a>Comentários  
 O valor de `moduleId` não é válido para uma solicitação de informações após o `ModuleUnloadStarted` método retornará – esta é a última oportunidade do criador de perfil para obter informações sobre este módulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ModuleUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
