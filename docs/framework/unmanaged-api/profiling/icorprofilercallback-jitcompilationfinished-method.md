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
ms.openlocfilehash: dbf447e1325b4acaa26c9bb16d7d1a736eb20a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
 [in] Um valor que indica o criador de perfil se bloqueio afetará a operação do tempo de execução. O valor é `true` se o bloqueio pode fazer com que o tempo de execução aguardar o thread de chamada de retorno de chamada de retorno; caso contrário, `false`.  
  
 Embora um valor de `true` não prejudicarão o tempo de execução, ele pode afetar os resultados da criação de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
