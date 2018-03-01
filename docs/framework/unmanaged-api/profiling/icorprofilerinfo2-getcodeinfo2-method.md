---
title: "Método ICorProfilerInfo2::GetCodeInfo2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b211ba79de7454361b44c6e9852ad6698c2e71c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>Método ICorProfilerInfo2::GetCodeInfo2
Obtém as extensões de código nativo associado ao `FunctionID`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionID`  
 [in] A ID da função à qual o código nativo está associado.  
  
 `cCodeInfos`  
 [in] O tamanho do `codeInfos` matriz.  
  
 `pcCodeInfos`  
 [out] Um ponteiro para o número total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) estruturas disponíveis.  
  
 `codeInfos`  
 [out] Um buffer fornecido pelo chamador. Depois que o método retorna, contém uma matriz de `COR_PRF_CODE_INFO` estruturas, cada um deles descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 As extensões são classificadas em ordem crescente deslocamento de linguagem intermediária (MSIL) do Microsoft.  
  
 Depois de `GetCodeInfo2` retorna, você deve verificar se o `codeInfos` buffer era grande o suficiente para conter todos o `COR_PRF_CODE_INFO` estruturas. Para fazer isso, comparar o valor de `cCodeInfos` com o valor de `cchName` parâmetro. Se `cCodeInfos` dividida pelo tamanho de um `COR_PRF_CODE_INFO` estrutura é menor do que `pcCodeInfos`, alocar uma maior `codeInfos` buffer, atualize `cCodeInfos` com o novo tamanho maior e chame `GetCodeInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo2` com um comprimento zero `codeInfos` buffer para obter o tamanho do buffer correto. Você pode definir o `codeInfos` de buffer de tamanho para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de um `COR_PRF_CODE_INFO` estrutura e chame `GetCodeInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
