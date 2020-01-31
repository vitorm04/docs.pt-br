---
title: Método ICorProfilerCallback2::GarbageCollectionStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865773"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>Método ICorProfilerCallback2::GarbageCollectionStarted
Notifica o criador de perfil de código que a coleta de lixo foi iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cGenerations`  
 no O número total de entradas na matriz de `generationCollected`.  
  
 `generationCollected`  
 no Uma matriz de valores Boolianos, que são `true` se a geração que corresponde ao índice de matriz está sendo coletada por essa coleta de lixo; caso contrário, `false`.  
  
 A matriz é indexada por um valor da enumeração [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , que indica a geração.  
  
 `reason`  
 no Um valor da enumeração [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) que indica o motivo pelo qual a coleta de lixo foi induzida.  
  
## <a name="remarks"></a>Comentários  
 Todos os retornos de chamada que pertencem a essa coleta de lixo ocorrerão entre o retorno de chamada `GarbageCollectionStarted` e o retorno de chamada [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) correspondente. Esses retornos de chamada não precisam ocorrer no mesmo thread.  
  
 É seguro que o criador de perfil Inspecione objetos em seus locais originais durante o retorno de chamada `GarbageCollectionStarted`. O coletor de lixo começará a mover objetos após o retorno de `GarbageCollectionStarted`. Depois que o criador de perfil for retornado desse retorno de chamada, o criador de perfil deverá considerar que todas as IDs de objeto sejam inválidas até receber um retorno de chamada `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](icorprofilercallback2-interface.md)
