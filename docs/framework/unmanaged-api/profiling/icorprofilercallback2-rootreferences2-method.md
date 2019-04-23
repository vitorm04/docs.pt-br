---
title: Método ICorProfilerCallback2::RootReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082146"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>Método ICorProfilerCallback2::RootReferences2
Notifica o criador de perfil sobre referências raiz após a ocorrência de uma coleta de lixo. Esse método é uma extensão de [ICorProfilerCallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 [in] O número de elementos na `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` matrizes.  
  
 `rootRefIds`  
 [in] Uma matriz de IDs de objeto, cada um deles faz referência a um objeto estático ou um objeto na pilha. Elementos na `rootKinds` matriz fornecem informações para classificar os elementos correspondentes no `rootRefIds` matriz.  
  
 `rootKinds`  
 [in] Uma matriz de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valores que indicam o tipo de raiz de coleta de lixo.  
  
 `rootFlags`  
 [in] Uma matriz de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valores que descrevem as propriedades de uma raiz de coleta de lixo.  
  
 `rootIds`  
 [in] Uma matriz de UINT_PTR valores que apontam para um inteiro que contém informações adicionais sobre a raiz de coleta de lixo, dependendo do valor da `rootKinds` parâmetro.  
  
 Se o tipo da raiz é uma pilha, a ID de raiz é para a função que contém a variável. Se essa ID de raiz for 0, a função é uma função sem nome que é interna ao CLR. Se o tipo da raiz é um identificador, a ID da raiz é o identificador da coleta de lixo. Para outros tipos de raiz, a ID é um valor opaco e deve ser ignorada.  
  
## <a name="remarks"></a>Comentários  
 O `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` matrizes são matrizes paralelas. Ou seja, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, e `rootIds[i]` todos dizem respeito a mesma raiz.  
  
 Ambos `RootReferences` e `RootReferences2` são chamados para notificar o criador de perfil. Criadores de perfil serão normalmente implementam um método ou a outra, mas não ambos, porque as informações passadas `RootReferences2` é um superconjunto do que passado `RootReferences`.  
  
 É possível que as entradas no `rootRefIds` como zero, o que implica que a referência raiz correspondente é nula e não faz referência a um objeto no heap gerenciado.  
  
 As IDs de objeto retornado por `RootReferences2` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`. Quando [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para os novos locais e pode ser inspecionados com segurança.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
