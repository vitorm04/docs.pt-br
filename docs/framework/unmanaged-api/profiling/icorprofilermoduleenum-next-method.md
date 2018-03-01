---
title: "Método ICorProfilerModuleEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fca8a0f999ccc497c1929faa6cead04a1ec2774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="135f3-102">Método ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="135f3-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="135f3-103">Obtém o número especificado de contíguos módulos de uma coleção sequencial de módulos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="135f3-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="135f3-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="135f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="135f3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="135f3-106">[in] O número de módulos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="135f3-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="135f3-107">[out] Uma matriz de `ModuleID` valores, cada um deles representa um módulo recuperado.</span><span class="sxs-lookup"><span data-stu-id="135f3-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="135f3-108">[out] Um ponteiro para o número de elementos realmente retornados no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="135f3-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="135f3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="135f3-109">Return Value</span></span>  
 <span data-ttu-id="135f3-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="135f3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="135f3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="135f3-111">HRESULT</span></span>|<span data-ttu-id="135f3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="135f3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="135f3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="135f3-113">S_OK</span></span>|<span data-ttu-id="135f3-114">`celt`elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="135f3-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="135f3-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="135f3-115">S_FALSE</span></span>|<span data-ttu-id="135f3-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="135f3-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="135f3-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="135f3-117">Requirements</span></span>  
 <span data-ttu-id="135f3-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="135f3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="135f3-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="135f3-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="135f3-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="135f3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="135f3-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="135f3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="135f3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="135f3-122">See Also</span></span>  
 [<span data-ttu-id="135f3-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="135f3-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="135f3-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="135f3-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
