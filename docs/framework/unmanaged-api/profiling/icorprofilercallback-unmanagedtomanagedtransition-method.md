---
title: Método ICorProfilerCallback::UnmanagedToManagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 421b729468cad365c48bccdae3b31132dd1ed894
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496017"
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
 [in] Um valor igual a [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeração que indica se a transição ocorreu devido a uma chamada para o código gerenciado do código não gerenciado, ou devido a um retorno de uma função não gerenciada chamado por um gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `reason` é COR_PRF_TRANSITION_RETURN e `functionId` não for nulo, a função ID é o de função não gerenciada e nunca foram compilado usando o compilador just-in-time (JIT). Funções não gerenciadas têm algumas informações básicas associadas a eles, como um nome e alguns metadados.  
  
 Se o valor de `reason` é COR_PRF_TRANSITION_CALL, talvez seja possível que a função de chamada (ou seja, a função gerenciada) ainda não foi compilado por JIT.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [Usando PInvoke explícito no C++ (atributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Usando interop do C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
