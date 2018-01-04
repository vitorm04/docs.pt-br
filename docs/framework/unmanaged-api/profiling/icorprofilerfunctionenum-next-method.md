---
title: "Método ICorProfilerFunctionEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd9c01e014ee19c5e30fdc293d39787638e8b1d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="6b661-102">Método ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6b661-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="6b661-103">Obtém o número especificado de funções de contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="6b661-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b661-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b661-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b661-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b661-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6b661-106">[in] O número de funções para recuperar.</span><span class="sxs-lookup"><span data-stu-id="6b661-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="6b661-107">[out] Uma matriz de `COR_PRF_FUNCTION` valores, cada um deles representa uma função recuperada.</span><span class="sxs-lookup"><span data-stu-id="6b661-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6b661-108">[out] Um ponteiro para o número de funções de fato retornadas no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="6b661-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b661-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6b661-109">Return Value</span></span>  
 <span data-ttu-id="6b661-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="6b661-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b661-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b661-111">HRESULT</span></span>|<span data-ttu-id="6b661-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b661-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b661-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b661-113">S_OK</span></span>|<span data-ttu-id="6b661-114">`celt`elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="6b661-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="6b661-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b661-115">S_FALSE</span></span>|<span data-ttu-id="6b661-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="6b661-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b661-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b661-117">Requirements</span></span>  
 <span data-ttu-id="6b661-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b661-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b661-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b661-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b661-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b661-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b661-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b661-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b661-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b661-122">See Also</span></span>  
 [<span data-ttu-id="6b661-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="6b661-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="6b661-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6b661-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
