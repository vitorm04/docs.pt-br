---
title: ICorDebugILCode2::Método GetInstrumentedILMap
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417896"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="6ec3e-102">ICorDebugILCode2::Método GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="6ec3e-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="6ec3e-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="6ec3e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6ec3e-104">Retorna um mapa dos deslocamentos da linguagem intermediária (IL) instrumentados pelo criador de perfis para os deslocamentos da IL do método original para esta instância.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec3e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ec3e-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ec3e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ec3e-106">Parameters</span></span>  
 <span data-ttu-id="6ec3e-107">cMap</span><span class="sxs-lookup"><span data-stu-id="6ec3e-107">cMap</span></span>  
 <span data-ttu-id="6ec3e-108">[in] A capacidade de armazenamento da matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="6ec3e-109">Consulte a seção Comentários para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="6ec3e-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="6ec3e-110">pcMap</span></span>  
 <span data-ttu-id="6ec3e-111">[out] O número de valores COR_IL_MAP gravado para a matriz de mapa.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="6ec3e-112">map</span><span class="sxs-lookup"><span data-stu-id="6ec3e-112">map</span></span>  
 <span data-ttu-id="6ec3e-113">[out] Uma matriz de valores COR_IL_MAP que fornecem informações sobre mapeamentos de IL instrumentado criador de perfil para o nível de integridade do método original.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ec3e-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ec3e-114">Remarks</span></span>  
 <span data-ttu-id="6ec3e-115">Se o criador de perfil define o mapeamento chamando o [: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) método, o depurador pode chamar esse método para recuperar o mapeamento e usar o mapeamento internamente ao calcular IL desloca para a pilha os rastreamentos e tempos de vida de variáveis.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="6ec3e-116">Se `cMap` é 0 e `pcMap` é não -**nulo**, `pcMap` é definido como o número de valores COR_IL_MAP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="6ec3e-117">Se `cMap` for não zero, representará a capacidade de armazenamento da matriz do `map`.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="6ec3e-118">Quando o método retorna, `map` conterá um máximo de `cMap` itens, e `pcMap` é definido como o número de valores COR_IL_MAP gravados a `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="6ec3e-119">Se a IL não tiver sido instrumentada ou o mapeamento não tiver sido fornecido por um criador de perfil, esse método retorna `S_OK` e define `pcMap` para 0.</span><span class="sxs-lookup"><span data-stu-id="6ec3e-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec3e-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ec3e-120">Requirements</span></span>  
 <span data-ttu-id="6ec3e-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec3e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec3e-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ec3e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ec3e-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ec3e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ec3e-124">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec3e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec3e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ec3e-125">See Also</span></span>  
 [<span data-ttu-id="6ec3e-126">: Setilinstrumentedcodemap</span><span class="sxs-lookup"><span data-stu-id="6ec3e-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [<span data-ttu-id="6ec3e-127">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="6ec3e-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="6ec3e-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6ec3e-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
