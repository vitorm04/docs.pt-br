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
ms.openlocfilehash: f7bc1954d11134a4515d2e29e9e0eb1626ae5d26
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863421"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>Método ICorProfilerInfo::SetEnterLeaveFunctionHooks
Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFuncEnter`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionEnter](functionenter-function.md) .  
  
 `pFuncLeave`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionLeave](functionleave-function.md) .  
  
 `pFuncTailcall`  
 no Um ponteiro para a implementação a ser usado como o retorno de chamada [FunctionTailcall](functiontailcall-function.md) .  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 1,0, cada ponteiro de função pode ser nulo para desabilitar esse retorno de chamada correspondente.  
  
 Somente um conjunto de retornos de chamada pode estar ativo por vez. Portanto, se um criador de perfil chamar `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` terá precedência.  
  
 O método `SetEnterLeaveFunctionHooks` pode ser chamado somente do retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do criador de perfil.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
