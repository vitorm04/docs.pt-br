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
ms.openlocfilehash: 164e042ab0f1a275ff07b917658024e22c2d7b0b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862017"
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
 no O tamanho da matriz de `codeInfos`.  
  
 `pcCodeInfos`  
 fora Um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.  
  
 `codeInfos`  
 fora Um buffer fornecido pelo chamador. Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 O método `GetCodeInfo3` é semelhante a [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), exceto pelo fato de que ele obterá a ID de compilação JIT recompilada da função que contém o endereço IP especificado.  
  
> [!NOTE]
> `GetCodeInfo3` pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) não vai. Para obter mais informações, consulte o [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).  
  
 Depois que `GetCodeInfo3` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`. Se `cCodeInfos` dividido pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo3` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) e chamar `GetCodeInfo3` novamente.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)
- [Interface ICorProfilerInfo4](icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
