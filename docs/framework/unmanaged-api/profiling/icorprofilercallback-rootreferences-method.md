---
title: "Método ICorProfilerCallback::RootReferences"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd057538450deeb46a72178c725103e04a8dd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a>Método ICorProfilerCallback::RootReferences
Notifica o criador de perfil com informações sobre referências da raiz após a coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 [in] O número de referências a `rootRefIds` matriz.  
  
 `rootRefIds`  
 [in] Uma matriz de IDs de objeto que fazem referência a um objeto estático ou um objeto na pilha.  
  
## <a name="remarks"></a>Comentários  
 Ambos `RootReferences` e [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) são chamados para notificar o criador de perfil. Criadores de perfil normalmente implementará um ou outro, mas não ambos, porque as informações transmitidas em `RootReferences2` é um superconjunto do passado `RootReferences`.  
  
 É possível que o `rootRefIds` matriz que contém um objeto nulo. Por exemplo, todas as referências de objeto declaradas na pilha são tratadas como raízes pelo coletor de lixo e sempre serão relatadas.  
  
 As IDs de objeto retornado por `RootReferences` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços. Portanto, criadores de perfil não devem tentar inspecionar objetos durante um `RootReferences` chamar. Quando [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e pode ser inspecionados com segurança.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
