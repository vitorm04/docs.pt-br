---
title: Método ICorProfilerInfo4::GetCodeInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912710"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>Método ICorProfilerInfo4::GetCodeInfo3
Obtém as extensões do código nativo associado à versão recompilada do JIT da função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionID`  
 no A ID da função à qual o código nativo está associado.  
  
 `reJitId`  
 no A identidade da função de compilação JIT recompilada.  
  
 `cCodeInfos`  
 no O tamanho da `codeInfos` matriz.  
  
 `pcCodeInfos`  
 fora Um ponteiro para o número total de estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponíveis.  
  
 `codeInfos`  
 fora Um buffer fornecido pelo chamador. Depois que o método retorna, ele contém uma matriz `COR_PRF_CODE_INFO` de estruturas, cada uma delas descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 O `GetCodeInfo3` método é semelhante a [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), exceto pelo fato de que ele receberá a ID de compilação JIT recompilada da função que contém o endereço IP especificado.  
  
> [!NOTE]
> `GetCodeInfo3`pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) não vai. Para obter mais informações, consulte o HRESULT do [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) .  
  
 As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).  
  
 Depois `GetCodeInfo3` de retornar, você deve verificar se `codeInfos` o buffer foi grande o suficiente para conter todas as estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . Para fazer isso, compare o valor de `cCodeInfos` com o valor `cchName` do parâmetro. Se `cCodeInfos` dividido pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) for menor que `pcCodeInfos`, aloque um buffer maior `codeInfos` , atualize `cCodeInfos` com o novo tamanho, maior e chame `GetCodeInfo3` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um buffer de comprimento `codeInfos` zero para obter o tamanho de buffer correto. Em seguida, você pode `codeInfos` definir o tamanho do buffer para o `pcCodeInfos`valor retornado em, multiplicado pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) e `GetCodeInfo3` chamar novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
