---
title: Método ICorProfilerInfo3::GetFunctionLeave3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862393"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>Método ICorProfilerInfo3::GetFunctionLeave3Info
Fornece o quadro de pilha e o valor de retorno da função que está sendo relatada ao criador de perfil pela função de [função FunctionLeave3WithInfo](functionleave3withinfo-function.md) . Esse método pode ser chamado somente durante o retorno de chamada `FunctionLeave3WithInfo`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A `FunctionID` da função que está retornando.  
  
 `eltInfo`  
 no Um identificador opaco que representa informações sobre um determinado registro de ativação. O criador de perfil deve fornecer o mesmo `eltInfo` fornecido ao criador de perfil pela função [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .  
  
 `pFrameInfo`  
 fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação. Esse identificador é válido somente durante o retorno de chamada `FunctionLeave3WithInfo` no qual o criador de perfil chamou o método `GetFunctionLeave3Info`.  
  
 `pRetvalRange`  
 fora Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) que contém o valor retornado da função. Para acessar informações de valor de retorno, o sinalizador de `COR_PRF_ENABLE_FUNCTION_RETVAL` deve ser definido. O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
