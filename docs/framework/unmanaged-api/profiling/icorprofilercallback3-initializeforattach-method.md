---
title: Método ICorProfilerCallback3::InitializeForAttach
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebdd76655124922008667898e38f873ad93598e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555590"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>Método ICorProfilerCallback3::InitializeForAttach
Chamado pelo common language runtime (CLR) para dar uma oportunidade de inicializar seu estado após uma operação de anexação de criador de perfil.  
  
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
 [in] Um ponteiro para os dados passados para o [iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método no seu `pvClientData` parâmetro. Se esse parâmetro for nulo, `cbClientData` será 0 (zero). O CLR libera essa memória quando ele retorna da `InitializeForAttach`.  
  
 `cbClientData`  
 [in] O tamanho, em bytes, dos dados que `pvClientData` aponta.  
  
## <a name="remarks"></a>Comentários  
 O CLR chama `InitializeForAttach` para dar o criador de perfil uma oportunidade para retornos de chamada de solicitação.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
