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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177014"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>Método ICorProfilerInfo3::GetFunctionEnter3Info
Fornece o quadro de pilha e as informações de argumento da função que está sendo relatada ao profiler pela função [FunctionEnter3WithInfo.](functionenter3withinfo-function.md) Este método só pode `FunctionEnter3WithInfo` ser chamado durante o retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>parâmetros  
 `functionId`  
 [em] A `FunctionID` função que está sendo inserida.  
  
 `eltInfo`  
 [em] Uma alça opaca que representa informações sobre um determinado quadro de pilha. O profiler deve `eltInfo` fornecer o mesmo que foi dado pela função [FunctionEnter3WithInfo.](functionenter3withinfo-function.md)  
  
 `pFrameInfo`  
 [fora] Uma alça opaca que representa informações genéricas sobre um determinado quadro de pilha. Esta alça é válida `FunctionEnter3WithInfo` somente durante o retorno `GetFunctionEnter3Info` de chamada no qual o profiler chamou o método.  
  
 `pcbArgumentInfo`  
 [dentro, fora] Um ponteiro para o tamanho total, em bytes, da estrutura [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (mais quaisquer estruturas [adicionais de COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) para as faixas de argumento apontadas por `pArgumentInfo`). Se o tamanho especificado não for suficiente, ERROR_INSUFFICIENT_BUFFER é `pcbArgumentInfo`devolvido e o tamanho esperado é armazenado em . Para `GetFunctionEnter3Info` ligar apenas para recuperar `*pcbArgumentInfo`o `*pcbArgumentInfo`valor `pArgumentInfo`esperado para , definir =0 e =NULL.  
  
 `pArgumentInfo`  
 [fora] Um ponteiro para uma estrutura [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que descreve os locais dos argumentos da função na memória, na ordem da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 O profiler deve alocar `COR_PRF_FUNCTION_ARGUMENT_INFO` espaço suficiente para a estrutura da função que `pcbArgumentInfo` está sendo inspecionada, e deve indicar o tamanho no parâmetro.  
  
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
