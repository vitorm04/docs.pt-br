---
title: Método ICorProfilerInfo4::GetReJITIDs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1055366576f45a7ca137b6d8170d1786c2ba4492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455335"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>Método ICorProfilerInfo4::GetReJITIDs
Retorna uma matriz de IDs de identificar todos os recompilado JIT versões da função especificada ainda alocados. Isso inclui versões recompilado JIT de funções que foram posteriormente revertidas, mas ainda não liberadas (por exemplo, quando o domínio de aplicativo que contém a função revertida ainda está em uso).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] O `FunctionID` da instância de função para o qual enumerar versões.  
  
 `cReJitIds`  
 [in] O número de IDs recompilado JIT alocados a `reJitIds` matriz.  
  
 `pcReJitIds`  
 [out] O número real de IDs de recompilação de JIT.  
  
 `reJitIds`  
 [out] Uma matriz alocada pelo chamador que conterá as IDs recompilado JIT para a função especificada.  
  
## <a name="remarks"></a>Comentários  
 `GetReJITIDs` Enumera as IDs de recompilado JIT ativas para uma instância de função determinada. Ele segue o mesmo padrão de uso como outros `ICorProfilerInfo` funções que aceitam buffers alocada pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
