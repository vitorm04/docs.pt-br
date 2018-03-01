---
title: "Método ICorProfilerCallback3::InitializeForAttach"
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
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 124e27e446e129173018aed9d3ab770582342c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a>Método ICorProfilerCallback3::InitializeForAttach
Chamado pelo common language runtime (CLR) para que o criador de perfil que tenha a oportunidade para inicializar o estado após uma operação de anexação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCorProfilerInfoUnk`  
 [in] Um ponteiro de interface para o `ICorProfilerInfo*` interface.  
  
 `pvClientData`  
 [in] Um ponteiro para os dados passados para o [Iclrprofiling](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método no seu `pvClientData` parâmetro. Se esse parâmetro for null, `cbClientData` será 0 (zero). O CLR libera memória quando ele retorna da `InitializeForAttach`.  
  
 `cbClientData`  
 [in] O tamanho, em bytes, dos dados que `pvClientData` aponta para.  
  
## <a name="remarks"></a>Comentários  
 O CLR chama `InitializeForAttach` para que o criador de perfil tenha a oportunidade para retornos de chamada de solicitação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
