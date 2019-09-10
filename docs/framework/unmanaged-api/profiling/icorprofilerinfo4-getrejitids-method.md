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
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855944"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>Método ICorProfilerInfo4::GetReJITIDs
Retorna uma matriz de IDs que identifica todas as versões recompiladas por JIT da função especificada que ainda estão alocadas. Isso inclui versões recompiladas do JIT de funções que foram revertidas posteriormente, mas ainda não foram liberadas (por exemplo, quando o domínio do aplicativo que contém a função revertida ainda estiver em uso).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no O `FunctionID` da instância de função para a qual enumerar versões.  
  
 `cReJitIds`  
 no O número de IDs recompiladas por JIT alocadas na `reJitIds` matriz.  
  
 `pcReJitIds`  
 fora O número real de IDs recompiladas por JIT.  
  
 `reJitIds`  
 fora Uma matriz alocada pelo chamador que conterá as IDs de compilação JIT recompiladas para a função especificada.  
  
## <a name="remarks"></a>Comentários  
 `GetReJITIDs`enumera as IDs de recompilação JIT ativas para uma determinada instância de função. Ele segue o mesmo padrão de uso que `ICorProfilerInfo` outras funções que aceitam buffers alocados pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
