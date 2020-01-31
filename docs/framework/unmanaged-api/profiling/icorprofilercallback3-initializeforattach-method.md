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
ms.openlocfilehash: d0219751987b1f2d78ee37a1553b323014c1ccfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865682"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>Método ICorProfilerCallback3::InitializeForAttach
Chamado pelo Common Language Runtime (CLR) para dar ao criador de perfil uma oportunidade de inicializar seu estado após uma operação de anexação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCorProfilerInfoUnk`  
 no Um ponteiro de interface para a interface `ICorProfilerInfo*`.  
  
 `pvClientData`  
 no Um ponteiro para os dados passados para o método [ICLRProfiling:: AttachProfiler](iclrprofiling-attachprofiler-method.md) em seu parâmetro `pvClientData`. Se esse parâmetro for nulo, `cbClientData` será 0 (zero). O CLR libera essa memória quando ela retorna da `InitializeForAttach`.  
  
 `cbClientData`  
 no O tamanho, em bytes, dos dados aos quais `pvClientData` aponta.  
  
## <a name="remarks"></a>Comentários  
 O CLR chama `InitializeForAttach` para dar ao criador de perfil uma oportunidade de solicitar retornos de chamada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
