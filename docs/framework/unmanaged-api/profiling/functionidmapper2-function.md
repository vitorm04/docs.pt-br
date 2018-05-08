---
title: Função FunctionIDMapper2
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92285d6aef41595fd4729aa82a827c3efc09b03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="functionidmapper2-function"></a>Função FunctionIDMapper2
Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) retornos de chamada para essa função. `FunctionIDMapper2` Também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] O identificador de função a ser remapeados.  
  
 `clientData`  
 [in] Um ponteiro para dados que são usados para resolver a ambiguidade entre os tempos de execução.  
  
 `pbHookFunction`  
 [out] Um ponteiro para um valor que define o criador de perfil para `true` se deseja receber `FunctionEnter3`, `FunctionLeave3`, e `FunctionTailcall3`, ou `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, e `FunctionTailcall3WithInfo` retornos de chamada; caso contrário, ele define esse valor como `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 O criador de perfil retorna um valor que usa o mecanismo de execução como um identificador de função alternativos. O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`. Caso contrário, um valor de retorno nulo produz resultados imprevisíveis, incluindo possivelmente interromper o processo.  
  
## <a name="remarks"></a>Comentários  
 Este método estende o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função com um parâmetro adicional que é usado para passar dados do cliente. Os dados do cliente são usados para resolver a ambiguidade entre os tempos de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [ICorProfilerInfo3::SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
