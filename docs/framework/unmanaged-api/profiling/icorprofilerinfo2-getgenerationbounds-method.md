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
ms.openlocfilehash: 310bde2889f8a383fde88cb1bbffce9bad157399
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267999"
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
  
## <a name="parameters"></a>Parâmetros  
 `cObjectRanges`  
 [in] O número de elementos alocada pelo chamador para o `ranges` matriz.  
  
 `pcObjectRanges`  
 [out] Um ponteiro para um inteiro que especifica o número total de intervalos de alguns ou todos os quais serão retornados o `ranges` matriz.  
  
 `ranges`  
 [out] Uma matriz de [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estruturas, cada um deles descreve um intervalo (ou seja, o bloco) de memória dentro a geração que está passando por coleta de lixo.  
  
## <a name="remarks"></a>Comentários  
 O `GetGenerationBounds` método pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não está em andamento.

 A maioria das mudança de gerações ocorre durante as coletas de lixo. Gerações podem crescer entre coleções, mas geralmente não mover ao redor. Portanto, os lugares mais interessantes para chamar `GetGenerationBounds` estão na `ICorProfilerCallback2::GarbageCollectionStarted` e `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Durante a inicialização do programa, alguns objetos são alocados pelo common language runtime (CLR) em si, geralmente em gerações 3 e 0. Assim, quando o código gerenciado inicia a execução, essas gerações já conterá objetos. Gerações 1 e 2 normalmente estarão vazias, exceto para objetos fictícios que são gerados pelo coletor de lixo. (O tamanho dos objetos fictícios é 12 bytes em implementações de 32 bits do CLR; o tamanho é maior em implementações de 64 bits). Você também poderá ver os intervalos de geração 2 que estão dentro de módulos produzidos pelo gerador de imagem nativa (NGen.exe). Nesse caso, os objetos na geração 2 são *congelado objetos*, que é alocado quando NGen.exe é executado em vez de pelo coletor de lixo.  
  
 Essa função usa buffers alocados pelo chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
