---
title: Método ICorProfilerInfo2::GetGenerationBounds
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cfac1304a3d60a418065e4fc2994705548eeac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458432"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>Método ICorProfilerInfo2::GetGenerationBounds
Obtém as regiões de memória, que são segmentos de heap, que compõem as várias gerações de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cObjectRanges`  
 [in] O número de elementos alocada pelo chamador para o `ranges` matriz.  
  
 `pcObjectRanges`  
 [out] Um ponteiro para um número inteiro que especifica o número total de intervalos, alguns ou todos os quais serão retornados o `ranges` matriz.  
  
 `ranges`  
 [out] Uma matriz de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estruturas, cada um deles descreve um intervalo (ou seja, o bloco) de memória dentro a geração que está passando por coleta de lixo.  
  
## <a name="remarks"></a>Comentários  
 O `GetGenerationBounds` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento. Ou seja, ele pode ser chamado de qualquer retorno de chamada, exceto os que ocorrem entre [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) e [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 A maioria dos mudando de gerações ocorre durante a coleta de lixo. Gerações podem crescer entre coleções, mas geralmente não mover. Portanto, os locais mais interessantes para chamar `GetGenerationBounds` no `ICorProfilerCallback2::GarbageCollectionStarted` e `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Durante a inicialização do programa, alguns objetos são alocados pelo common language runtime (CLR), geralmente em gerações 3 e 0. Assim, quando o código gerenciado inicia a execução, essas gerações já contém objetos. Gerações 1 e 2 normalmente estará vazias, exceto para objetos fictícios que são gerados pelo coletor de lixo. (O tamanho dos objetos fictícios será de 12 bytes em implementações de 32 bits do CLR; o tamanho é maior em implementações de 64 bits). Você também poderá ver os intervalos de geração 2 dentro de módulos produzidos pelo gerador de imagem nativa (NGen.exe). Nesse caso, os objetos na geração 2 são *congelado objetos*, que é alocado quando NGen.exe é executado em vez de pelo coletor de lixo.  
  
 Essa função usa buffers alocada pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
