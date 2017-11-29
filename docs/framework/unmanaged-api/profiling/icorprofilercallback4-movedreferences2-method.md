---
title: "Método ICorProfilerCallback4::MovedReferences2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.MovedReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8137d944081475095509150cce84a611b7030eb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4movedreferences2-method"></a>Método ICorProfilerCallback4::MovedReferences2
Chamado para o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação de relatório. Este método é chamado se o criador de perfil tiver implementado o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. Esse retorno de chamada substitui o [: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, porque ela pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expressa em um ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cMovedObjectIDRanges`  
 [in] O número de blocos de contíguos objetos que movidas como o resultado de compactação da coleta de lixo. Ou seja, o valor de `cMovedObjectIDRanges` é o tamanho total do `oldObjectIDRangeStart`, `newObjectIDRangeStart`, e `cObjectIDRangeLength` matrizes.  
  
 Os próximos três argumentos de `MovedReferences2` matrizes paralelos. Em outras palavras, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, e `cObjectIDRangeLength[i]` todos diz respeito a um único bloco de objetos adjacentes.  
  
 `oldObjectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o antigo (coleta de lixo pré-lançamento) Iniciando endereço de um bloco de contígua, live objetos na memória.  
  
 `newObjectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o novo endereço inicial (coleta de pós-lixo) de um bloco de contígua, live objetos na memória.  
  
 `cObjectIDRangeLength`  
 [in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco de objetos contíguos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado no `oldObjectIDRangeStart` e `newObjectIDRangeStart` matrizes.  
  
## <a name="remarks"></a>Comentários  
 Um coletor de lixo compactação recupera a memória ocupada por objetos inativos e compacta que liberado espaço. Como resultado, os objetos em tempo real podem ser movidos no heap, e `ObjectID` valores distribuídos por meio de notificações anteriores podem ser alterado.  
  
 Suponha que um existente `ObjectID` valor (`oldObjectID`) está dentro do seguinte intervalo:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Nesse caso, o deslocamento do início do intervalo para o início do objeto é o seguinte:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Para qualquer valor de `i` que está no seguinte intervalo:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 Você pode calcular o novo `ObjectID` da seguinte maneira:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Nenhum do `ObjectID` valores passados pelo `MovedReferences2` são válidos durante o retorno de chamada em si, porque o coletor de lixo pode estar no meio de mover objetos de locais antigos para novos locais. Portanto, os criadores de perfis não devem tentar inspecionar objetos durante uma chamada `MovedReferences2`. Um [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) retorno de chamada indica que todos os objetos foram movidos para seus novos locais e inspeção pode ser executada.  
  
 Se o criador de perfil implementa ambos o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `MovedReferences2` método é chamado antes do [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) método, mas somente se o `MovedReferences2` método retorna com êxito. Criadores de perfil podem retornar um HRESULT que indica uma falha do `MovedReferences2` método para evitar o segundo método de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
