---
title: Método ICorProfilerCallback::JITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530743"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>Método ICorProfilerCallback::JITCompilationFinished
Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a compilação de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que foi compilada.  
  
 `hrStatus`  
 [in] Um valor que indica se a compilação foi bem-sucedida.  
  
 `fIsSafeToBlock`  
 [in] Um valor que indica o criador de perfil, se o bloqueio afetará a operação de tempo de execução. O valor será `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno desse retorno de chamada; caso contrário, `false`.  
  
 Embora um valor de `true` não danificará o tempo de execução, ele pode afetar os resultados de criação de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
