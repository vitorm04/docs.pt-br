---
title: Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: 4fe18b4f07e6f282571b13faff5ce51b66ce416b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868480"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a>Método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
Especifica as funções implementadas pelo criador de perfil que serão chamadas nos ganchos [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) das funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFuncEnter3`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionEnter3WithInfo`.  
  
 `pFuncLeave3`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionLeave3WithInfo`.  
  
 `pFuncTailcall3`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada `FunctionTailcall3WithInfo`.  
  
## <a name="remarks"></a>Comentários  
 Os ganchos [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) fornecem inspeção de quadro de pilha e de argumentos. Para acessar essas informações, os sinalizadores `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`e/ou `COR_PRF_ENABLE_FRAME_INFO` devem ser definidos. O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o método `SetEnterLeaveFunctionHooks3WithInfo` para registrar a implementação dessa função.  
  
 Somente um conjunto de retornos de chamada pode estar ativo por vez e a versão mais recente tem precedência. Portanto, se um criador de perfil chamar [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) e `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` será usado.  
  
 O método `SetEnterLeaveFunctionHooks3WithInfo` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
