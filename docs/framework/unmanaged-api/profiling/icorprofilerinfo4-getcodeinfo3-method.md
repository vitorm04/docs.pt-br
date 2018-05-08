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
ms.openlocfilehash: cebf5f1101abed29bc325cec2390b4fd13056e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>Método ICorProfilerInfo4::GetCodeInfo3
Obtém as extensões de código nativo associado com a versão recompilada JIT da função especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionID`  
 [in] A ID da função à qual o código nativo está associado.  
  
 `reJitId`  
 [in] A identidade da função recompilado JIT.  
  
 `cCodeInfos`  
 [in] O tamanho do `codeInfos` matriz.  
  
 `pcCodeInfos`  
 [out] Um ponteiro para o número total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas disponíveis.  
  
 `codeInfos`  
 [out] Um buffer fornecido pelo chamador. Depois que o método retorna, contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada um deles descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 O `GetCodeInfo3` método é semelhante ao [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), exceto que ele receberá o ID recompilado JIT da função que contém o endereço IP especificado.  
  
> [!NOTE]
>  `GetCodeInfo3` pode disparar uma coleta de lixo, enquanto [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) não. Para obter mais informações, consulte o [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 As extensões são classificadas em ordem crescente de deslocamento comuns CIL (Intermediate Language).  
  
 Depois de `GetCodeInfo3` retorna, você deve verificar se o `codeInfos` buffer era grande o suficiente para conter todos o [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas. Para fazer isso, comparar o valor de `cCodeInfos` com o valor de `cchName` parâmetro. Se `cCodeInfos` dividida pelo tamanho de um [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estrutura é menor do que `pcCodeInfos`, alocar uma maior `codeInfos` buffer, atualize `cCodeInfos` com o novo tamanho maior e chame `GetCodeInfo3` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo3` com um comprimento zero `codeInfos` buffer para obter o tamanho do buffer correto. Você pode definir o `codeInfos` de buffer de tamanho para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de um [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estrutura e chame `GetCodeInfo3` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
