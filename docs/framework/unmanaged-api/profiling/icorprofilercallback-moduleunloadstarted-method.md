---
title: Método ICorProfilerCallback::ModuleUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c509606995a0ddb00a8b586ce8b8cd54b7694cd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452504"
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
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ModuleUnloadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
