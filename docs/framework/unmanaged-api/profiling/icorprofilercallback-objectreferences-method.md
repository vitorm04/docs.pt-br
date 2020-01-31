---
title: Método ICorProfilerCallback::ObjectReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866085"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>Método ICorProfilerCallback::ObjectReferences
Notifica o criador de perfil sobre objetos na memória que estão sendo referenciados pelo objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 no A ID do objeto que está fazendo referência a objetos.  
  
 `classId`  
 no A ID da classe da qual o objeto especificado é uma instância do.  
  
 `cObjectRefs`  
 no O número de objetos referenciados pelo objeto especificado (ou seja, o número de elementos na matriz de `objectRefIds`).  
  
 `objectRefIds`  
 no Uma matriz de IDs de objetos que estão sendo referenciados por `objectId`.  
  
## <a name="remarks"></a>Comentários  
 O método `ObjectReferences` é chamado para cada objeto restante no heap após a conclusão de uma coleta de lixo. Se o criador de perfil retornar um erro desse retorno de chamada, os serviços de criação de perfil descontinuarão invocando esse retorno de chamada até a próxima coleta de lixo.  
  
 O retorno de chamada `ObjectReferences` pode ser usado em conjunto com o retorno de chamada [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) para criar um grafo de referência de objeto completo para o tempo de execução. O Common Language Runtime (CLR) garante que cada referência de objeto seja relatada apenas uma vez pelo método `ObjectReferences`.  
  
 As IDs de objeto retornadas por `ObjectReferences` não são válidas durante o próprio retorno de chamada, pois a coleta de lixo pode estar no meio da movimentação de objetos. Portanto, os profileres não devem tentar inspecionar objetos durante uma chamada de `ObjectReferences`. Quando [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, a coleta de lixo é concluída e a inspeção pode ser feita com segurança.  
  
 Um `ClassId` nulo indica que `objectId` tem um tipo que está descarregando.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
