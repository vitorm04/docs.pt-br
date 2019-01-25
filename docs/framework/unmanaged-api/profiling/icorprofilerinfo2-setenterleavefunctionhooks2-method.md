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
ms.openlocfilehash: bb7c8fa40d260e45ae536f1b58c6ab360f35448e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550637"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
Especifica as funções implementada pelo criador de perfil a ser chamada nas versões atualizadas do "enter", "Sair" e "chamada tail" ganchos de funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada.  
  
 `pFuncLeave`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada.  
  
 `pFuncTailcall`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retorno de chamada.  
  
## <a name="remarks"></a>Comentários  
 O `SetEnterLeaveFunctionHooks2` método é semelhante de [ICorProfilerInfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) método. Use a primeira opção para especificar funções a serem usadas como as versões mais recentes de enter/deixar/tailcall retornos de chamada e o segundo para especificar as funções a serem usadas como as versões mais antigas dos retornos de chamada enter/deixar/chamada tail.  
  
 Apenas um conjunto de retornos de chamada pode estar ativo por vez. Portanto, se um criador de perfil chama ambos `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` é usado.  
  
 O `SetEnterLeaveFunctionHooks2` método pode ser chamado apenas do criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
