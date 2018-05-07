---
title: Método ICorProfilerCallback::JITCachedFunctionSearchFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89c7b0fe0f3ade3f57aa50b100bc9b4ecc904a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>Método ICorProfilerCallback::JITCachedFunctionSearchFinished
Notifica o criador de perfil que uma pesquisa foi concluída para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para a qual a pesquisa foi realizada.  
  
 `result`  
 [in] Um valor de [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeração que indica o resultado da pesquisa.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 2.0, o [: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) e `JITCachedFunctionSearchFinished` retornos de chamada não serão feitos para todas as funções em imagens NGen normais. Somente imagens NGen otimizadas para um criador de perfil irá gerar retornos de chamada para todas as funções na imagem. No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil com otimização de NGen imagens somente se pretender usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT). Caso contrário, o criador de perfil deve usar uma estratégia lenta para reunir informações de função.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
