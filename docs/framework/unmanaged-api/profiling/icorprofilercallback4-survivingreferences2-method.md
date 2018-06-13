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
ms.openlocfilehash: de081286096a9001ff48b565baeb47a1d1a4f28a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460334"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>Método ICorProfilerCallback4::SurvivingReferences2
Relata o layout dos objetos no heap como resultado de uma coleta de lixo não compactar. Este método é chamado se o criador de perfil tiver implementado o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. Esse retorno de chamada substitui o [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, porque ela pode relatar intervalos maiores de objetos cujos comprimentos excedem o que pode ser expressa em um ULONG.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cSurvivingObjectIDRanges`  
 [in] O número de blocos de contíguos objetos que sobreviveram como resultado da coleta de lixo não compactar. Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.  
  
 Os dois argumentos de `SurvivingReferences2` matrizes paralelos. Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` do mesmo bloco de contíguos objetos estão relacionados.  
  
 `objectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contígua, live objetos na memória.  
  
 `cObjectIDRangeLength`  
 [in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de contíguos objetos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.  
  
## <a name="remarks"></a>Comentários  
 Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo. Suponha que um `ObjectID` valor (`ObjectID`) está dentro do seguinte intervalo:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobreviveu a coleta de lixo:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uma coleta de lixo não compactar recupera a memória ocupada por objetos "inativos", mas não compactar o que o espaço livre. Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.  
  
 O common language runtime (CLR) chama `SurvivingReferences2` para não compactar coletas de lixo. Para compactar coletas de lixo, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) é chamado em vez disso. Uma coleta de lixo único pode ser compactação para uma geração e não compactar para outro. Para uma coleta de lixo na geração qualquer específica, o criador de perfil será exibido um `SurvivingReferences2` retorno de chamada ou uma [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) retorno de chamada, mas não ambos.  
  
 Vários `SurvivingReferences2` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários retornos de chamada durante a coleta de lixo do servidor e outros motivos. No caso de vários retornos de chamadas durante uma coleta de lixo, as informações são cumulativas; todas as referências são relatadas em qualquer `SurvivingReferences2` retorno de chamada sobreviver a coleta de lixo.  
  
 Se o criador de perfil implementa ambos o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, o `SurvivingReferences2` método é chamado antes do [ICorProfilerCallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) método, mas somente se `SurvivingReferences2` retorna com êxito. Criadores de perfil podem retornar um HRESULT que indica falha a partir de `SurvivingReferences2` método para evitar o segundo método de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
