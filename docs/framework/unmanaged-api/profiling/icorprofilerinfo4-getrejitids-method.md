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
ms.openlocfilehash: 0361a4cd048f0b3be6bce47e52dd44ba3cea3475
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482750"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>Método ICorProfilerInfo4::GetReJITIDs
Retorna uma matriz de IDs que identificam todos os recompilado por JIT versões da função especificada que ainda são alocadas. Isso inclui versões recompilado por JIT funções que foram revertidas, posteriormente, mas ainda não liberadas (por exemplo, quando o domínio do aplicativo que contém a função revertida ainda está em uso).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] O `FunctionID` da instância de função para o qual será enumerada versões.  
  
 `cReJitIds`  
 [in] O número de IDs recompilado por JIT alocados a `reJitIds` matriz.  
  
 `pcReJitIds`  
 [out] O número real de IDs recompilado por JIT.  
  
 `reJitIds`  
 [out] Uma matriz alocada pelo chamador que conterá as IDs recompilado por JIT para a função especificada.  
  
## <a name="remarks"></a>Comentários  
 `GetReJITIDs` Enumera as IDs de recompilado por JIT Active Directory para uma instância de função determinada. Ele segue o mesmo padrão de uso como outro `ICorProfilerInfo` funções que aceitam buffers alocados pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
