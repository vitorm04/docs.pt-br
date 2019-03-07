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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cda3230c652efeffa4a599849ba13dca1e5039b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472285"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>Método ICorProfilerCallback4::SurvivingReferences2
Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação. Esse método é chamado se o criador de perfil tiver implementado a [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. Esse retorno de chamada substitui o [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, porque ele pode relatar intervalos maiores de objetos cujo comprimento excede o que pode ser expresso em um ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cSurvivingObjectIDRanges`  
 [in] O número de blocos contíguos objetos que sobreviveram como resultado da coleta de lixo sem compactação. Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.  
  
 Os próximos dois argumentos de `SurvivingReferences2` são matrizes paralelas. Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` referem-se do mesmo bloco de objetos contíguos.  
  
 `objectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contíguos, live objetos na memória.  
  
 `cObjectIDRangeLength`  
 [in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de objetos adjacentes na memória.  
  
 Um tamanho for especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.  
  
## <a name="remarks"></a>Comentários  
 Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo. Suponha que um `ObjectID` valor (`ObjectID`) se encontra dentro do seguinte intervalo:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobrevive à coleta de lixo:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uma coleta de lixo sem compactação recupera a memória ocupada por objetos "inativos", mas não compacta que o espaço livre. Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.  
  
 O common language runtime (CLR) chama `SurvivingReferences2` para coletas de lixo sem compactação. Para compactação coletas de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso. Uma coleta de lixo único pode ser compactação para uma geração e sem compactação para outro. Para uma coleta de lixo de qualquer geração específica, o criador de perfil serão recebê-las uma `SurvivingReferences2` retorno de chamada ou um [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) retorno de chamada, mas não ambos.  
  
 Vários `SurvivingReferences2` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários retornos de chamada durante a coleta de lixo do servidor e outros motivos. No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas; todas as referências que são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobreviver a coleta de lixo.  
  
 Se o criador de perfis implementa ambos os [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `SurvivingReferences2` método é chamado antes do [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, mas somente se `SurvivingReferences2` retorna com êxito. Os criadores de perfis podem retornar um HRESULT que indica uma falha do `SurvivingReferences2` método para evitar o segundo método de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
