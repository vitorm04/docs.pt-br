---
title: "Método ICorProfilerCallback::ObjectReferences"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30b8f6b5f424ff81ace36baa8d2ae39e0a2f1d1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a>Método ICorProfilerCallback::ObjectReferences
Notifica o criador de perfil sobre objetos na memória que está sendo referenciado pelo objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `objectId`  
 [in] A ID do objeto que faz referência a objetos.  
  
 `classId`  
 [in] A ID da classe que o objeto especificado for uma instância do.  
  
 `cObjectRefs`  
 [in] O número de objetos referenciados pelo objeto especificado (ou seja, o número de elementos a `objectRefIds` matriz).  
  
 `objectRefIds`  
 [in] Uma matriz de IDs de objetos que estão sendo referenciados por `objectId`.  
  
## <a name="remarks"></a>Comentários  
 O `ObjectReferences` método é chamado para cada objeto restantes no heap após uma coleta de lixo. Se o criador de perfil retorna um erro desse retorno de chamada, os serviços de criação de perfil serão Descontinuado invocar esse retorno de chamada até a próxima coleta de lixo.  
  
 O `ObjectReferences` retorno de chamada pode ser usado em conjunto com o [: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) retorno de chamada para criar um gráfico de referência de objeto completo para o tempo de execução. O common language runtime (CLR) garante que cada referência de objeto é relatada somente uma vez pelo `ObjectReferences` método.  
  
 As IDs de objeto retornado por `ObjectReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de movimentação de objetos. Portanto, criadores de perfil não devem tentar inspecionar objetos durante um `ObjectReferences` chamar. Quando [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, o lixo coleção está concluída e inspeção pode ser feita com segurança.  
  
 Um valor nulo `ClassId` indica que `objectId` tem um tipo que está descarregando.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
