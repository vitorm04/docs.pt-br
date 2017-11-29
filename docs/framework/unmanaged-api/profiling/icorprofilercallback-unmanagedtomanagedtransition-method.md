---
title: "Método ICorProfilerCallback::UnmanagedToManagedTransition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.UnmanagedToManagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a2ceb53263e317c5c72695d6bc1e93f8f70bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>Método ICorProfilerCallback::UnmanagedToManagedTransition
Notifica o criador de perfil que ocorreu uma transição de código não gerenciado para código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que está sendo chamada.  
  
 `reason`  
 [in] Um valor de [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeração que indica se a transição ocorreu devido a uma chamada para código gerenciado em código não gerenciado, ou devido a um retorno de uma função não gerenciada chamado por um gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `reason` é COR_PRF_TRANSITION_RETURN e `functionId` é não nulo, a função ID é que a função não gerenciada e nunca foram compilado usando o compilador just-in-time (JIT). Funções não gerenciadas têm algumas informações básicas associadas a eles, como um nome e alguns metadados.  
  
 Se o valor de `reason` é COR_PRF_TRANSITION_CALL, é possível que a função de chamada (ou seja, a função gerenciada) ainda não foi compilada por JIT.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [Usando PInvoke explícito no C++ (atributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [Usando interop do C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
