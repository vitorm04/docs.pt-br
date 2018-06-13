---
title: Método ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0735e4c59ba609ed87d61aca737c4f8a4dab757a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453480"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>Método ICorProfilerCallback::ManagedToUnmanagedTransition
Notifica o criador de perfil que ocorreu uma transição de código gerenciado para código não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função que está sendo chamada.  
  
 `reason`  
 [in] Um valor de [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeração que indica se a transição ocorreu devido a uma chamada para código não gerenciado de código gerenciado, ou devido a um retorno de uma função gerenciada chamado por um não gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `reason` é COR_PRF_TRANSITION_CALL, a função ID é que a função não gerenciado, que nunca foram compilado usando o compilador just-in-time. Funções não gerenciadas têm informações básicas associadas a eles, como um nome e alguns metadados. Se a função não gerenciada foi chamada com o uso de plataforma implícita invocar (PInvoke), o tempo de execução não é possível determinar o destino da chamada e o valor de `functionId` será nulo. Para obter mais informações sobre PInvoke implícita, consulte [usando Interop C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [Usando PInvoke explícito no C++ (atributo DllImport)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
