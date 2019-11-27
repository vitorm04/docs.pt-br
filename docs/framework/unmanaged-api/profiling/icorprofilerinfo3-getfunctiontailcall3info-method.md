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
ms.openlocfilehash: e7a25fce945504cff0d07f499ae4bb79378e9f3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449694"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>Método ICorProfilerInfo3::GetFunctionTailcall3Info
Fornece o quadro de pilha da função que está sendo reportada para o criador de perfil pela função [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) . Esse método pode ser chamado somente durante o retorno de chamada `FunctionTailcall3WithInfo`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A `FunctionID` da função que está retornando.  
  
 `eltInfo`  
 no Um identificador opaco que representa informações sobre um determinado registro de ativação. O criador de perfil deve fornecer o mesmo `eltInfo` fornecido ao criador de perfil pela função `FunctionTailcall3WithInfo`.  
  
 `pFrameInfo`  
 fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação. Esse identificador é válido somente durante o retorno de chamada `FunctionTailcall3WithInfo` no qual o criador de perfil chamou o método `GetFunctionTailcall3Info`.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
