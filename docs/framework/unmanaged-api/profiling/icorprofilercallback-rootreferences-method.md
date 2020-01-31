---
title: Método ICorProfilerCallback::RootReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865955"
---
# <a name="icorprofilercallbackrootreferences-method"></a>Método ICorProfilerCallback::RootReferences
Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 no O número de referências na matriz de `rootRefIds`.  
  
 `rootRefIds`  
 no Uma matriz de IDs de objeto que fazem referência a um objeto estático ou a um objeto na pilha.  
  
## <a name="remarks"></a>Comentários  
 Tanto `RootReferences` quanto [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) são chamados para notificar o criador de perfil. Os profileres normalmente implementarão um ou outro, mas não ambos, porque as informações transmitidas `RootReferences2` são um superconjunto do passado `RootReferences`.  
  
 É possível que a matriz de `rootRefIds` contenha um objeto nulo. Por exemplo, todas as referências de objeto declaradas na pilha são tratadas como raízes pelo coletor de lixo e sempre serão relatadas.  
  
 As IDs de objeto retornadas por `RootReferences` não são válidas durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos de endereços antigos para novos endereços. Portanto, os profileres não devem tentar inspecionar objetos durante uma chamada de `RootReferences`. Quando [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e podem ser inspecionados com segurança.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
