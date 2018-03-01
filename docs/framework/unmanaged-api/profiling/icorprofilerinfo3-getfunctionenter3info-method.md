---
title: "Método ICorProfilerInfo3::GetFunctionEnter3Info"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b7053f526d415dbaef872e37d139d25ae5ac462
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>Método ICorProfilerInfo3::GetFunctionEnter3Info
Fornece as informações de pilha quadro e o argumento da função que está sendo relatada para o criador de perfil, o [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função. Esse método pode ser chamado somente durante o `FunctionEnter3WithInfo` retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] O `FunctionID` da função que está sendo inserida.  
  
 `eltInfo`  
 [in] Um identificador opaco que representa informações sobre um determinado registro de ativação. O criador de perfil deve fornecer as mesmas `eltInfo` que foi fornecido pelo [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função.  
  
 `pFrameInfo`  
 [out] Um identificador opaco que representa informações de genéricos sobre um determinado registro de ativação. Esse identificador é válido somente durante o `FunctionEnter3WithInfo` que o criador de perfil de chamada de retorno de chamada a `GetFunctionEnter3Info` método.  
  
 `pcbArgumentInfo`  
 [out no] Um ponteiro para o tamanho total, em bytes, do [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura (mais adicionais [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estruturas para os intervalos de argumento apontadas pelo `pArgumentInfo`). Se o tamanho especificado não é suficiente, ERROR_INSUFFICIENT_BUFFER será retornada e o tamanho esperado é armazenado em `pcbArgumentInfo`. Para chamar `GetFunctionEnter3Info` apenas para recuperar o valor esperado de `*pcbArgumentInfo`, defina `*pcbArgumentInfo`= 0 e `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura que descreve os locais dos argumentos da função na memória, em ordem da esquerda para direita.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil deve alocar espaço suficiente para o `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura da função que está sendo inspecionada e deve indicar o tamanho no `pcbArgumentInfo` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
