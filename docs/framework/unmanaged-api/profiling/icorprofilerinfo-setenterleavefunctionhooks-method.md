---
title: "Método ICorProfilerInfo::SetEnterLeaveFunctionHooks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2bf897ce41e2d9a8b4c7b9eeb4053ea0e9ad951
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>Método ICorProfilerInfo::SetEnterLeaveFunctionHooks
Especifica as funções implementada pelo criador de perfil a ser chamado no "entrar", "Sair" e "tailcall" ganchos de funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) retorno de chamada.  
  
 `pFuncLeave`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) retorno de chamada.  
  
 `pFuncTailcall`  
 [in] Um ponteiro para a implementação para ser usado como o [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) retorno de chamada.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 1.0, cada ponteiro de função pode ser nulo para desabilitar o retorno de chamada correspondente.  
  
 Apenas um conjunto de retornos de chamada pode estar ativo por vez. Portanto, se um criador de perfil chama ambos `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), em seguida, `SetEnterLeaveFunctionHooks2` terá precedência.  
  
 O `SetEnterLeaveFunctionHooks` método pode ser chamado somente a partir do criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
