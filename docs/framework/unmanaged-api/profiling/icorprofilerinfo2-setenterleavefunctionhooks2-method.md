---
title: Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52988378ff4df0bb03e15c9a4b25efbcd6c318f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
Especifica as funções implementada pelo criador de perfil a ser chamado nas versões atualizadas de "entrar", "Sair" e "tailcall" ganchos de funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada.  
  
 `pFuncLeave`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada.  
  
 `pFuncTailcall`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retorno de chamada.  
  
## <a name="remarks"></a>Comentários  
 O `SetEnterLeaveFunctionHooks2` método é semelhante do [Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) método. Use o primeiro para especificar funções a serem usadas como as versões mais recentes dos retornos de chamada deixe/enter/tailcall e o segundo para especificar funções a serem usadas como as versões mais antigas de retornos de chamada de licença/enter/tailcall.  
  
 Apenas um conjunto de retornos de chamada pode estar ativo por vez. Portanto, se um criador de perfil chama ambos `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` é usado.  
  
 O `SetEnterLeaveFunctionHooks2` método pode ser chamado somente a partir do criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
