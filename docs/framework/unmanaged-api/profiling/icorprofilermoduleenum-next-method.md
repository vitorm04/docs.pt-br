---
title: "Método ICorProfilerModuleEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="1e1dd-102">Método ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="1e1dd-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="1e1dd-103">Obtém o número especificado de contíguos módulos de uma coleção sequencial de módulos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e1dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e1dd-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e1dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e1dd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1e1dd-106">[in] O número de módulos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="1e1dd-107">[out] Uma matriz de `ModuleID` valores, cada um deles representa um módulo recuperado.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1e1dd-108">[out] Um ponteiro para o número de elementos realmente retornados no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e1dd-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1e1dd-109">Return Value</span></span>  
 <span data-ttu-id="1e1dd-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1e1dd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e1dd-111">HRESULT</span></span>|<span data-ttu-id="1e1dd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e1dd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e1dd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e1dd-113">S_OK</span></span>|<span data-ttu-id="1e1dd-114">`celt`elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="1e1dd-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1e1dd-115">S_FALSE</span></span>|<span data-ttu-id="1e1dd-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="1e1dd-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e1dd-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e1dd-117">Requirements</span></span>  
 <span data-ttu-id="1e1dd-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e1dd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e1dd-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e1dd-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e1dd-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e1dd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e1dd-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e1dd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1dd-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e1dd-122">See Also</span></span>  
 [<span data-ttu-id="1e1dd-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="1e1dd-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="1e1dd-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1e1dd-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
