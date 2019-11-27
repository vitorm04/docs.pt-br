---
title: Método ICorProfilerCallback4::SurvivingReferences2
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: 3178d099db96d52f0238cfcf7e055e761687ce30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430089"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>Método ICorProfilerCallback4::SurvivingReferences2
Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação. Esse método será chamado se o criador de perfil tiver implementado a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) . Esse retorno de chamada substitui o método [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) , pois ele pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expresso em ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cSurvivingObjectIDRanges`  
 no O número de blocos de objetos contíguos que sobreviveram como resultado da coleta de lixo sem compactação. Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho das matrizes `objectIDRangeStart` e `cObjectIDRangeLength`, que armazenam um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.  
  
 Os dois próximos argumentos de `SurvivingReferences2` são matrizes paralelas. Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` se preocupam com o mesmo bloco de objetos contíguos.  
  
 `objectIDRangeStart`  
 no Uma matriz de valores de `ObjectID`, cada um dos quais é o endereço inicial de um bloco de objetos dinâmicos contíguos na memória.  
  
 `cObjectIDRangeLength`  
 no Uma matriz de inteiros, cada qual é o tamanho de um bloco sobrevivente de objetos contíguos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado na matriz de `objectIDRangeStart`.  
  
## <a name="remarks"></a>Comentários  
 Os elementos das matrizes `objectIDRangeStart` e `cObjectIDRangeLength` devem ser interpretados da seguinte maneira para determinar se um objeto sobreviveram a coleta de lixo. Suponha que um valor de `ObjectID` (`ObjectID`) está dentro do seguinte intervalo:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Para qualquer valor de `i` que esteja no seguinte intervalo, o objeto tem sobreviveram a coleta de lixo:  
  
 0 < = `i` < `cSurvivingObjectIDRanges`  
  
 Uma coleta de lixo não compactada recupera a memória ocupada por objetos "inativos", mas não compacta esse espaço livre. Como resultado, a memória é retornada para o heap, mas nenhum objeto "ao vivo" é movido.  
  
 O Common Language Runtime (CLR) chama `SurvivingReferences2` para coletas de lixo sem compactação. Para compactar as coleções de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso. Uma única coleta de lixo pode ser compactada para uma geração e não compactação para outra. Para uma coleta de lixo em qualquer geração específica, o criador de perfil receberá um `SurvivingReferences2` retorno de chamada ou um retorno de chamada [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) , mas não ambos.  
  
 Vários retornos de chamada de `SurvivingReferences2` podem ser recebidos durante uma coleta de lixo específica, devido ao buffer interno limitado, a vários retornos de chamada durante a coleta de lixo do servidor e por outros motivos. No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas; todas as referências que são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobrevivem à coleta de lixo.  
  
 Se o criador de perfil implementar as interfaces [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) , o método `SurvivingReferences2` será chamado antes do método [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) , mas somente se `SurvivingReferences2` retornar com êxito. Os profileres podem retornar um HRESULT que indica falha do método `SurvivingReferences2` para evitar chamar o segundo método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
