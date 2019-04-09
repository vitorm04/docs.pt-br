---
title: Método ICorProfilerInfo3::GetFunctionEnter3Info
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164821"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>Método ICorProfilerInfo3::GetFunctionEnter3Info
Fornece as informações de quadro e o argumento de pilha da função que está sendo relatada ao criador de perfil, o [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função. Esse método pode ser chamado somente durante o `FunctionEnter3WithInfo` retorno de chamada.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] O `FunctionID` da função que está sendo inserida.  
  
 `eltInfo`  
 [in] Um identificador opaco que representa informações sobre um registro de ativação. O criador de perfil deve fornecer os mesmos `eltInfo` que foi fornecido pelo [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função.  
  
 `pFrameInfo`  
 [out] Um identificador opaco que representa as informações sobre um registro de ativação genéricos. Esse identificador é válido somente durante o `FunctionEnter3WithInfo` retorno de chamada em que o criador de perfil chamado o `GetFunctionEnter3Info` método.  
  
 `pcbArgumentInfo`  
 [no, out] Um ponteiro para o tamanho total, em bytes, do [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura (além de outras [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estruturas para os intervalos de argumento apontados pelo `pArgumentInfo`). Se o tamanho especificado não é suficiente, ERROR_INSUFFICIENT_BUFFER é retornado e o tamanho esperado é armazenado no `pcbArgumentInfo`. Para chamar `GetFunctionEnter3Info` apenas para recuperar o valor esperado `*pcbArgumentInfo`, defina `*pcbArgumentInfo`= 0 e `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura que descreve os locais dos argumentos da função na memória, em ordem da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil deve alocar espaço suficiente para o `COR_PRF_FUNCTION_ARGUMENT_INFO` estrutura da função que está sendo inspecionada e deve indicar o tamanho no `pcbArgumentInfo` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Criação de perfil de interfaces](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
