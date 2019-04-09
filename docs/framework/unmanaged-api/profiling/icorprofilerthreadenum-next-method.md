---
title: Método ICorProfilerThreadEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44595229eaefa0d8fc8ca7bf15a88d0fbf1ee0d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104306"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="c484f-102">Método ICorProfilerThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="c484f-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="c484f-103">Obtém o número especificado de threads contíguos de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="c484f-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c484f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c484f-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c484f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c484f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c484f-106">[in] O número de threads para recuperar.</span><span class="sxs-lookup"><span data-stu-id="c484f-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="c484f-107">[out] Uma matriz de `ThreadID` valores, cada um deles representa um thread recuperado.</span><span class="sxs-lookup"><span data-stu-id="c484f-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c484f-108">[out] Um ponteiro para o número de threads, na verdade, é retornado no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="c484f-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c484f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c484f-109">Return Value</span></span>  
 <span data-ttu-id="c484f-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="c484f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c484f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c484f-111">HRESULT</span></span>|<span data-ttu-id="c484f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c484f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c484f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c484f-113">S_OK</span></span>|`celt` <span data-ttu-id="c484f-114">elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="c484f-114">elements were returned.</span></span>|  
|<span data-ttu-id="c484f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c484f-115">S_FALSE</span></span>|<span data-ttu-id="c484f-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="c484f-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c484f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c484f-117">Requirements</span></span>  
 <span data-ttu-id="c484f-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c484f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c484f-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c484f-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c484f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c484f-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c484f-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c484f-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c484f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c484f-122">See also</span></span>

- [<span data-ttu-id="c484f-123">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="c484f-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="c484f-124">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="c484f-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
