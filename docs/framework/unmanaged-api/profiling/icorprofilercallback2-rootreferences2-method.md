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
ms.openlocfilehash: abf92749e1139a85ea2f49fb5d5caff69ce39c24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458455"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>Método ICorProfilerCallback2::RootReferences2
Notifica o criador de perfil sobre referências da raiz após a conclusão de uma coleta de lixo. Esse método é uma extensão do [: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cRootRefs`  
 [in] O número de elementos de `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` matrizes.  
  
 `rootRefIds`  
 [in] Uma matriz de IDs de objeto, cada um deles faz referência a um objeto estático ou um objeto na pilha. Elementos de `rootKinds` matriz fornecem informações para classificar os elementos correspondentes na `rootRefIds` matriz.  
  
 `rootKinds`  
 [in] Uma matriz de [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) valores que indicam o tipo de raiz de coleta de lixo.  
  
 `rootFlags`  
 [in] Uma matriz de [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) valores que descrevem as propriedades de uma raiz de coleta de lixo.  
  
 `rootIds`  
 [in] Uma matriz de UINT_PTR valores que aponte para um número inteiro que contém informações adicionais sobre a raiz de coleta de lixo, dependendo do valor da `rootKinds` parâmetro.  
  
 Se o tipo da raiz é uma pilha, a ID de raiz é a função que contém a variável. Se essa ID de raiz for 0, a função é uma função sem nome interna para o CLR. Se o tipo da raiz é um identificador, a ID de raiz é o identificador de coleta de lixo. Para outros tipos de raiz, a ID é um valor opaco e deve ser ignorada.  
  
## <a name="remarks"></a>Comentários  
 O `rootRefIds`, `rootKinds`, `rootFlags`, e `rootIds` as matrizes são matrizes paralelos. Ou seja, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, e `rootIds[i]` todas envolvem a mesma raiz.  
  
 Ambos `RootReferences` e `RootReferences2` são chamados para notificar o criador de perfil. Criadores de perfil normalmente implementar um método ou o outro, mas não ambos, porque as informações transmitidas em `RootReferences2` é um superconjunto do passado `RootReferences`.  
  
 É possível que as entradas em `rootRefIds` como zero, o que implica que a referência de raiz correspondente é nula e não se refere a um objeto no heap gerenciado.  
  
 As IDs de objeto retornado por `RootReferences2` não são válidos durante o retorno de chamada em si, porque a coleta de lixo pode estar no meio de mover objetos de endereços antigos para novos endereços. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `RootReferences2`. Quando [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) é chamado, todos os objetos foram movidos para seus novos locais e pode ser inspecionados com segurança.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
