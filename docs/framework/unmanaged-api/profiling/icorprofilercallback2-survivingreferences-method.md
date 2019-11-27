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
ms.openlocfilehash: a83f8566dfe8e1b612f67d95a0e69947b72704ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439601"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>Método ICorProfilerCallback2::SurvivingReferences
Relata o layout dos objetos no heap como resultado de uma coleta de lixo sem compactação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cSurvivingObjectIDRanges`  
 no O número de blocos de objetos contíguos que sobreviveram como resultado da coleta de lixo sem compactação. Ou seja, o valor de `cSurvivingObjectIDRanges` é o tamanho das matrizes `objectIDRangeStart` e `cObjectIDRangeLength`, que armazenam um `ObjectID` e um comprimento, respectivamente, para cada bloco de objetos.  
  
 Os dois próximos argumentos de `SurvivingReferences` são matrizes paralelas. Em outras palavras, `objectIDRangeStart` e `cObjectIDRangeLength` se preocupam com o mesmo bloco de objetos contíguos.  
  
 `objectIDRangeStart`  
 no Uma matriz de valores de `ObjectID`, cada um dos quais é o endereço inicial de um bloco de objetos dinâmicos contíguos na memória.  
  
 `cObjectIDRangeLength`  
 no Uma matriz de inteiros, cada qual é o tamanho de um bloco sobrevivente de objetos contíguos na memória.  
  
 Um tamanho é especificado para cada bloco que é referenciado na matriz de `objectIDRangeStart`.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Esse método relata tamanhos como `MAX_ULONG` para objetos maiores que 4 GB em plataformas de 64 bits. Para objetos com mais de 4 GB, use o método [ICorProfilerCallback4:: SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) em vez disso.  
  
 Os elementos das matrizes `objectIDRangeStart` e `cObjectIDRangeLength` devem ser interpretados da seguinte maneira para determinar se um objeto sobreviveram a coleta de lixo. Suponha que um valor de `ObjectID` (`ObjectID`) está dentro do seguinte intervalo:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Para qualquer valor de `i` que esteja no seguinte intervalo, o objeto tem sobreviveram a coleta de lixo:  
  
 0 < = `i` < `cSurvivingObjectIDRanges`  
  
 Uma coleta de lixo não compactada recupera a memória ocupada por objetos "inativos", mas não compacta esse espaço livre. Como resultado, a memória é retornada para o heap, mas nenhum objeto "ao vivo" é movido.  
  
 O Common Language Runtime (CLR) chama `SurvivingReferences` para coletas de lixo sem compactação. Para compactar as coleções de lixo, [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) é chamado em vez disso. Uma única coleta de lixo pode ser compactada para uma geração e não compactação para outra. Para uma coleta de lixo em qualquer geração específica, o criador de perfil receberá um retorno de chamada `SurvivingReferences` ou um `MovedReferences` retorno de chamada, mas não ambos.  
  
 Vários retornos de chamada de `SurvivingReferences` podem ser recebidos durante uma coleta de lixo específica, devido a buffers internos limitados, vários threads relatando no caso da coleta de lixo do servidor e por outros motivos. No caso de vários retornos de chamada durante uma coleta de lixo, as informações são cumulativas — todas as referências que são relatadas em qualquer `SurvivingReferences` retorno de chamada sobrevivem à coleta de lixo.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [Método SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
