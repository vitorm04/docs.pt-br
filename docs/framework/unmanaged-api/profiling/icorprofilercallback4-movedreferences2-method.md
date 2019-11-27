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
ms.openlocfilehash: 37d5f5e8294bb87a8796d6dcae046864904b096b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439379"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>Método ICorProfilerCallback4::MovedReferences2
Chamado para relatar o novo layout de objetos no heap como resultado de uma coleta de lixo de compactação. Esse método será chamado se o criador de perfil tiver implementado a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) . Esse retorno de chamada substitui o método [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) , pois ele pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expresso em ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cMovedObjectIDRanges`  
 no O número de blocos de objetos contíguos que foram movidos como resultado da coleta de lixo de compactação. Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total das matrizes `oldObjectIDRangeStart`, `newObjectIDRangeStart`e `cObjectIDRangeLength`.  
  
 Os próximos três argumentos de `MovedReferences2` são matrizes paralelas. Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`e `cObjectIDRangeLength[i]` se preocupam com um único bloco de objetos contíguos.  
  
 `oldObjectIDRangeStart`  
 no Uma matriz de valores de `ObjectID`, cada um dos quais é o endereço inicial (coleta antes de lixo) de um bloco de objetos dinâmicos contíguos na memória.  
  
 `newObjectIDRangeStart`  
 no Uma matriz de valores de `ObjectID`, cada um dos quais é o novo endereço inicial (coleta de lixo) de um bloco de objetos dinâmicos contíguos na memória.  
  
 `cObjectIDRangeLength`  
 no Uma matriz de inteiros, cada qual é o tamanho de um bloco de objetos contíguos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado nas matrizes `oldObjectIDRangeStart` e `newObjectIDRangeStart`.  
  
## <a name="remarks"></a>Comentários  
 Um coletor de lixo de compactação recupera a memória ocupada por objetos inativos e compacta o espaço livre. Como resultado, os objetos dinâmicos podem ser movidos dentro do heap e `ObjectID` valores distribuídos por notificações anteriores podem ser alterados.  
  
 Suponha que um valor de `ObjectID` existente (`oldObjectID`) está dentro do seguinte intervalo:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Nesse caso, o deslocamento do início do intervalo até o início do objeto é o seguinte:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Para qualquer valor de `i` que esteja no seguinte intervalo:  
  
 0 < = `i` < `cMovedObjectIDRanges`  
  
 Você pode calcular o novo `ObjectID` da seguinte maneira:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Nenhum dos valores de `ObjectID` passados por `MovedReferences2` são válidos durante o próprio retorno de chamada, pois o coletor de lixo pode estar no meio da movimentação de objetos de locais antigos para novos locais. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`. Um retorno de chamada [ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) indica que todos os objetos foram movidos para seus novos locais e a inspeção pode ser executada.  
  
 Se o criador de perfil implementar as interfaces [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) , o método `MovedReferences2` será chamado antes do método [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) , mas somente se o método `MovedReferences2` retornar com êxito. Os profileres podem retornar um HRESULT que indica falha do método `MovedReferences2`, para evitar chamar o segundo método.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
