---
title: "Método ICorProfilerThreadEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3295f3dc9af50fb62a2008f59819a51a6032a48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="dae1a-102">Método ICorProfilerThreadEnum::Next</span><span class="sxs-lookup"><span data-stu-id="dae1a-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="dae1a-103">Obtém o número especificado de threads de contíguas de uma coleção sequencial de threads, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="dae1a-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dae1a-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dae1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dae1a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dae1a-106">[in] O número de threads para recuperar.</span><span class="sxs-lookup"><span data-stu-id="dae1a-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="dae1a-107">[out] Uma matriz de `ThreadID` valores, cada um deles representa um segmento recuperado.</span><span class="sxs-lookup"><span data-stu-id="dae1a-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dae1a-108">[out] Um ponteiro para o número de threads de fato retornadas no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="dae1a-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dae1a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dae1a-109">Return Value</span></span>  
 <span data-ttu-id="dae1a-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="dae1a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dae1a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dae1a-111">HRESULT</span></span>|<span data-ttu-id="dae1a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dae1a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dae1a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="dae1a-113">S_OK</span></span>|<span data-ttu-id="dae1a-114">`celt`elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="dae1a-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="dae1a-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dae1a-115">S_FALSE</span></span>|<span data-ttu-id="dae1a-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="dae1a-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dae1a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dae1a-117">Requirements</span></span>  
 <span data-ttu-id="dae1a-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae1a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae1a-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dae1a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dae1a-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dae1a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dae1a-121">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae1a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae1a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dae1a-122">See Also</span></span>  
 [<span data-ttu-id="dae1a-123">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="dae1a-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="dae1a-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="dae1a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
