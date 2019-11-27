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
ms.openlocfilehash: 8c4e132b90fa1f51bc6f858d75c159af212ec019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439897"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>Método ICorProfilerCallback::UnmanagedToManagedTransition
Notifica o criador de perfil de que uma transição de código não gerenciado para código gerenciado ocorreu.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função que está sendo chamada.  
  
 `reason`  
 no Um valor da enumeração [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) que indica se a transição ocorreu devido a uma chamada em código gerenciado a partir de código não gerenciado ou por causa de um retorno de uma função não gerenciada chamada por um gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `reason` for COR_PRF_TRANSITION_RETURN e `functionId` não for NULL, a ID da função será a da função não gerenciada e nunca terá sido compilada usando o compilador JIT (just-in-time). As funções não gerenciadas têm algumas informações básicas associadas a elas, como um nome e alguns metadados.  
  
 Se o valor de `reason` for COR_PRF_TRANSITION_CALL, talvez seja possível que a função chamada (ou seja, a função gerenciada) ainda não tenha sido compilada por JIT.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [Usando PInvoke explícito no C++ (atributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [Usando interop do C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
