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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b616017745d7cc33d57b1626b6c27c59a0a60a32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992284"
---
# <a name="icorprofilercallbackrootreferences-method"></a>Método ICorProfilerCallback::RootReferences
Notifica o criador de perfil com informações sobre referências raiz após a coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 [in] O número de referências no `rootRefIds` matriz.  
  
 `rootRefIds`  
 [in] Uma matriz de IDs de objetos que fazem referência a um objeto estático ou um objeto na pilha.  
  
## <a name="remarks"></a>Comentários  
 Ambos `RootReferences` e [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) são chamados para notificar o criador de perfil. Os criadores de perfis normalmente implementará um ou outro, mas não ambos, porque as informações passadas `RootReferences2` é um superconjunto do que passado `RootReferences`.  
  
 É possível que o `rootRefIds` matriz para conter um objeto nulo. Por exemplo, todas as referências de objeto declaradas na pilha são tratadas como raízes pelo coletor de lixo e sempre serão relatadas.  
  
 As IDs de objeto retornado por `RootReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante um `RootReferences` chamar. Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para os novos locais e pode ser inspecionados com segurança.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
