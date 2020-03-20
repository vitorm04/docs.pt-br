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
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176988"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>Método ICorProfilerInfo3::GetFunctionTailcall3Info
Fornece o quadro de pilha da função que está sendo relatada ao profiler pela função [FunctionTailcall3WithInfo.](functiontailcall3withinfo-function.md) Este método só pode `FunctionTailcall3WithInfo` ser chamado durante o retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>parâmetros  
 `functionId`  
 [em] A `FunctionID` função que está voltando.  
  
 `eltInfo`  
 [em] Uma alça opaca que representa informações sobre um determinado quadro de pilha. O profiler deve `eltInfo` fornecer o mesmo que foi `FunctionTailcall3WithInfo` dado ao profiler pela função.  
  
 `pFrameInfo`  
 [fora] Uma alça opaca que representa informações genéricas sobre um determinado quadro de pilha. Esta alça é válida `FunctionTailcall3WithInfo` somente durante o retorno `GetFunctionTailcall3Info` de chamada no qual o profiler chamou o método.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Functionenter3withinfo](functionenter3withinfo-function.md)
- [Functionleave3withinfo](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo](functiontailcall3withinfo-function.md)
- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Criação de perfil de interfaces](profiling-interfaces.md)
- [Criação de perfil](index.md)
