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
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433118"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="93dfe-102">Método ICorProfilerInfo2::GetGenerationBounds</span><span class="sxs-lookup"><span data-stu-id="93dfe-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="93dfe-103">Obtém as regiões de memória, que são segmentos do heap, que compõem as várias gerações de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="93dfe-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93dfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93dfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93dfe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93dfe-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="93dfe-106">no O número de elementos alocados pelo chamador para a matriz de `ranges`.</span><span class="sxs-lookup"><span data-stu-id="93dfe-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="93dfe-107">fora Um ponteiro para um inteiro que especifica o número total de intervalos, alguns ou todos os quais serão retornados na matriz de `ranges`.</span><span class="sxs-lookup"><span data-stu-id="93dfe-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="93dfe-108">fora Uma matriz de estruturas [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) , cada uma delas descreve um intervalo (ou seja, bloco) de memória na geração que está passando pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="93dfe-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93dfe-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="93dfe-109">Remarks</span></span>  
 <span data-ttu-id="93dfe-110">O método `GetGenerationBounds` pode ser chamado de qualquer retorno de chamada do criador de perfil, desde que a coleta de lixo não esteja em andamento.</span><span class="sxs-lookup"><span data-stu-id="93dfe-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="93dfe-111">A maior mudança das gerações ocorre durante as coletas de lixo.</span><span class="sxs-lookup"><span data-stu-id="93dfe-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="93dfe-112">As gerações podem crescer entre as coleções, mas geralmente não se movimentam.</span><span class="sxs-lookup"><span data-stu-id="93dfe-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="93dfe-113">Portanto, os lugares mais interessantes para chamar `GetGenerationBounds` estão em `ICorProfilerCallback2::GarbageCollectionStarted` e `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="93dfe-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="93dfe-114">Durante a inicialização do programa, alguns objetos são alocados pelo Common Language Runtime (CLR) em si, geralmente nas gerações 3 e 0.</span><span class="sxs-lookup"><span data-stu-id="93dfe-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="93dfe-115">Portanto, quando o código gerenciado de tempo começa a ser executado, essas gerações já conterão objetos.</span><span class="sxs-lookup"><span data-stu-id="93dfe-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="93dfe-116">As gerações 1 e 2 normalmente estarão vazias, exceto objetos fictícios gerados pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="93dfe-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="93dfe-117">(O tamanho dos objetos fictícios é de 12 bytes em implementações de 32 bits do CLR; o tamanho é maior em implementações de 64 bits.) Você também pode ver intervalos de geração 2 que estão dentro de módulos produzidos pelo gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="93dfe-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="93dfe-118">Nesse caso, os objetos na geração 2 são *objetos congelados*, que são alocados quando NGen. exe é executado em vez de pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="93dfe-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="93dfe-119">Essa função usa buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="93dfe-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93dfe-120">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="93dfe-120">Requirements</span></span>  
 <span data-ttu-id="93dfe-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93dfe-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93dfe-122">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="93dfe-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93dfe-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93dfe-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93dfe-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93dfe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dfe-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93dfe-125">See also</span></span>

- [<span data-ttu-id="93dfe-126">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="93dfe-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="93dfe-127">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="93dfe-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="93dfe-128">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="93dfe-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="93dfe-129">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="93dfe-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
