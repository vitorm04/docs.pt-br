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
ms.openlocfilehash: 55411f187e2ef73997633d94b37a7d5d2cfd74c9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868558"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>Método ICorProfilerInfo3::GetFunctionEnter3Info
Fornece o quadro de pilha e as informações de argumento da função que está sendo relatada para o criador de perfil pela função [FunctionEnter3WithInfo](functionenter3withinfo-function.md) . Esse método pode ser chamado somente durante o retorno de chamada `FunctionEnter3WithInfo`.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no O `FunctionID` da função que está sendo inserida.  
  
 `eltInfo`  
 no Um identificador opaco que representa informações sobre um determinado registro de ativação. O criador de perfil deve fornecer o mesmo `eltInfo` que foi fornecido pela função [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 fora Um identificador opaco que representa informações genéricas sobre um determinado registro de ativação. Esse identificador é válido somente durante o retorno de chamada `FunctionEnter3WithInfo` no qual o criador de perfil chamou o método `GetFunctionEnter3Info`.  
  
 `pcbArgumentInfo`  
 [entrada, saída] Um ponteiro para o tamanho total, em bytes, da estrutura de [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (mais quaisquer estruturas de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) adicionais para os intervalos de argumentos apontados por `pArgumentInfo`). Se o tamanho especificado não for suficiente, ERROR_INSUFFICIENT_BUFFER será retornado e o tamanho esperado será armazenado em `pcbArgumentInfo`. Para chamar `GetFunctionEnter3Info` apenas para recuperar o valor esperado para `*pcbArgumentInfo`, defina `*pcbArgumentInfo`= 0 e `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 fora Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que descreve os locais dos argumentos da função na memória, na ordem da esquerda para a direita.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil deve alocar espaço suficiente para a estrutura de `COR_PRF_FUNCTION_ARGUMENT_INFO` da função que está sendo inspecionada e deve indicar o tamanho no parâmetro `pcbArgumentInfo`.  
  
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
