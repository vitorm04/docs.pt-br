---
title: Método ICorProfilerCallback4::MovedReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d368c88503853d0620f28f02f88a6d887c1aa681
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156397"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>Método ICorProfilerCallback4::MovedReferences2
Chamado para relatar o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação. Esse método é chamado se o criador de perfil tiver implementado a [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. Esse retorno de chamada substitui o [ICorProfilerCallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, porque ele pode relatar intervalos maiores de objetos cujo comprimento excede o que pode ser expresso em um ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cMovedObjectIDRanges`  
 [in] O número de blocos de objetos contíguos que movidas como resultado da compactação coleta de lixo. Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total do `oldObjectIDRangeStart`, `newObjectIDRangeStart`, e `cObjectIDRangeLength` matrizes.  
  
 Os próximos três argumentos de `MovedReferences2` são matrizes paralelas. Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, e `cObjectIDRangeLength[i]` todos dizem respeito a um único bloco de objetos contíguos.  
  
 `oldObjectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o antigo (coleta de lixo de pré-lançamento) endereço de um bloco de contíguos inicial, os objetos dinâmicos na memória.  
  
 `newObjectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o novo endereço inicial (coleta de pós-lixo) de um bloco de contíguos, live objetos na memória.  
  
 `cObjectIDRangeLength`  
 [in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco de objetos adjacentes na memória.  
  
 Um tamanho for especificado para cada bloco que é referenciado na `oldObjectIDRangeStart` e `newObjectIDRangeStart` matrizes.  
  
## <a name="remarks"></a>Comentários  
 Um compactação coletor de lixo recupera a memória ocupada por objetos inativos e compacta que liberado espaço. Como resultado, os objetos em tempo real podem ser movidos no heap, e `ObjectID` valores distribuídos por meio de notificações anteriores pode ser alterado.  
  
 Suponha que uma já existente `ObjectID` valor (`oldObjectID`) se encontra dentro do seguinte intervalo:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Nesse caso, o deslocamento do início do intervalo para o início do objeto é da seguinte maneira:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Para qualquer valor de `i` que está no seguinte intervalo:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Você pode calcular o novo `ObjectID` da seguinte maneira:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Nenhum dos `ObjectID` valores passados pelo `MovedReferences2` são válidos durante o retorno de chamada em si, porque o coletor de lixo pode estar no meio de movimentação de objetos de locais antigos para novos locais. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`. Um [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada indica que todos os objetos foram movidos para os novos locais e inspeção pode ser executada.  
  
 Se o criador de perfis implementa ambos os [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `MovedReferences2` método é chamado antes do [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, mas somente se o `MovedReferences2` método retorna com êxito. Os criadores de perfis podem retornar um HRESULT que indica uma falha do `MovedReferences2` método, para evitar que o segundo método de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Criação de perfil de interfaces](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
