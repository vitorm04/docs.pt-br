---
title: Método ICorProfilerInfo3::GetFunctionTailcall3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c78d22c6566b49e85a59e4a682fa256d2d83ea3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455579"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>Método ICorProfilerInfo3::GetFunctionTailcall3Info
Fornece o quadro de pilhas da função que está sendo relatado para o criador de perfil, o [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) função. Esse método pode ser chamado somente durante o `FunctionTailcall3WithInfo` retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] O `FunctionID` da função que está retornando.  
  
 `eltInfo`  
 [in] Um identificador opaco que representa informações sobre um determinado registro de ativação. O criador de perfil deve fornecer as mesmas `eltInfo` que foi fornecido para o criador de perfil, o `FunctionTailcall3WithInfo` função.  
  
 `pFrameInfo`  
 [out] Um identificador opaco que representa informações de genéricos sobre um determinado registro de ativação. Esse identificador é válido somente durante o `FunctionTailcall3WithInfo` que o criador de perfil de chamada de retorno de chamada a `GetFunctionTailcall3Info` método.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
