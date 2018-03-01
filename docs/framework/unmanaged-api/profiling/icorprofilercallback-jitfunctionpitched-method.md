---
title: "Método ICorProfilerCallback::JITFunctionPitched"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48432911d7844e6519689961c985da37219179a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>Método ICorProfilerCallback::JITFunctionPitched
Notifica o criador de perfil que uma função que tenha sido just-in-time (JIT)-compilado foi removido da memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que foi removida.  
  
## <a name="remarks"></a>Comentários  
 Se a função removida é chamada, o criador de perfil receberá novos eventos de compilação JIT quando a função é recompilada. Atualmente, o compilador JIT common language runtime (CLR) não remove funções de memória, para que esse retorno de chamada não está sendo usado e não será recebido pelo criador de perfil.  
  
 O valor de `functionId` não é válido até que a função é recompilada. Quando a função é recompilada, o mesmo `functionId` valor será usado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
