---
title: Método ICorProfilerCallback2::SurvivingReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0ed1dc09e8dcee8a4c67e01279c6e13661e252d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback2survivingreferences-method"></a>Método ICorProfilerCallback2::SurvivingReferences
Relata o layout dos objetos no heap como resultado de uma coleta de lixo não compactar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cSurvivingObjectIDRanges`  
 [in] O número de blocos de contíguos objetos que sobreviveram como resultado da coleta de lixo não compactar. Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes, qual repositório um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.  
  
 Os dois argumentos de `SurvivingReferences` matrizes paralelos. Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` do mesmo bloco de contíguos objetos estão relacionados.  
  
 `objectIDRangeStart`  
 [in] Uma matriz de `ObjectID` valores, cada um deles é o endereço inicial de um bloco de contígua, live objetos na memória.  
  
 `cObjectIDRangeLength`  
 [in] Uma matriz de inteiros, cada um deles é o tamanho de um bloco sobrevivente de contíguos objetos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado no `objectIDRangeStart` matriz.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
>  Esse método informa os tamanhos como `MAX_ULONG` para objetos que são maiores do que 4 GB em plataformas de 64 bits. Para objetos que são maiores do que 4 GB, use o [ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) método em vez disso.  
  
 Os elementos do `objectIDRangeStart` e `cObjectIDRangeLength` matrizes devem ser interpretadas da seguinte maneira para determinar se um objeto sobreviveu a coleta de lixo. Suponha que um `ObjectID` valor (`ObjectID`) está dentro do seguinte intervalo:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Para qualquer valor de `i` que está no intervalo a seguir, o objeto sobreviveu a coleta de lixo:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uma coleta de lixo não compactar recupera a memória ocupada por objetos "inativos", mas não compactar o que o espaço livre. Como resultado, memória é retornada para o heap, mas não há objetos "ativos" são movidos.  
  
 O common language runtime (CLR) chama `SurvivingReferences` para não compactar coletas de lixo. Para compactar coletas de lixo, [: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) é chamado em vez disso. Uma coleta de lixo único pode ser compactação para uma geração e não compactar para outro. Para uma coleta de lixo na geração qualquer específica, o criador de perfil será exibido um `SurvivingReferences` retorno de chamada ou uma `MovedReferences` retorno de chamada, mas não ambos.  
  
 Vários `SurvivingReferences` retornos de chamada podem ser recebidos durante uma coleta de lixo específico, devido a buffer interno limitado, vários threads reporting no caso de coleta de lixo do servidor e por outros motivos. No caso de vários retornos de chamadas durante uma coleta de lixo, as informações são cumulativas – todas as referências são relatadas em qualquer `SurvivingReferences` retorno de chamada sobreviver a coleta de lixo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Método SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
