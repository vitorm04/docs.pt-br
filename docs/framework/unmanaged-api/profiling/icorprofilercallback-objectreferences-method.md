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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942266"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>Método ICorProfilerCallback::ObjectReferences
Notifica o criador de perfil sobre os objetos na memória que está sendo referenciado pelo objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 [in] A ID do objeto que faz referência a objetos.  
  
 `classId`  
 [in] A ID da classe que o objeto especificado é uma instância do.  
  
 `cObjectRefs`  
 [in] O número de objetos referenciados pelo objeto especificado (ou seja, o número de elementos no `objectRefIds` matriz).  
  
 `objectRefIds`  
 [in] Uma matriz de IDs de objetos que estão sendo referenciadas por `objectId`.  
  
## <a name="remarks"></a>Comentários  
 O `ObjectReferences` método é chamado para cada objeto restante no heap após uma coleta de lixo. Se o criador de perfil retornará um erro desse retorno de chamada, os serviços de criação de perfil serão Descontinuado invocar esse retorno de chamada até a próxima coleta de lixo.  
  
 O `ObjectReferences` retorno de chamada pode ser usado em conjunto com o [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) retorno de chamada para criar um gráfico de referência de objeto completo para o tempo de execução. O common language runtime (CLR) garante que cada referência de objeto é relatada somente uma vez pelo `ObjectReferences` método.  
  
 As IDs de objeto retornado por `ObjectReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de movimentação de objetos. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante um `ObjectReferences` chamar. Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, o lixo coleção for concluída e a inspeção pode ser feita com segurança.  
  
 Um valor nulo `ClassId` indica que `objectId` tem um tipo que está descarregando.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
