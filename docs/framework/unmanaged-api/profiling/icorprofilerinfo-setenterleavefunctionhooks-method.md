---
title: Método ICorProfilerInfo::SetEnterLeaveFunctionHooks
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5ad57c3a5523494ce0384e665764bc02f679e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547417"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>Método ICorProfilerInfo::SetEnterLeaveFunctionHooks
Especifica as funções implementada pelo criador de perfil a ser chamado no "enter", "Sair" e "chamada tail" ganchos de funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) retorno de chamada.  
  
 `pFuncLeave`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) retorno de chamada.  
  
 `pFuncTailcall`  
 [in] Um ponteiro para a implementação a ser usado como o [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) retorno de chamada.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 1.0, cada ponteiro de função pode ser nulo para desabilitar esse retorno de chamada correspondente.  
  
 Apenas um conjunto de retornos de chamada pode ser ativo por vez. Assim, se um criador de perfil chama ambos `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), em seguida, `SetEnterLeaveFunctionHooks2` terá precedência.  
  
 O `SetEnterLeaveFunctionHooks` método pode ser chamado apenas do criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
