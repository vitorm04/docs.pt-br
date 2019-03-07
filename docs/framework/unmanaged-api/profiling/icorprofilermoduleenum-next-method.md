---
title: Método ICorProfilerModuleEnum::Next
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b16a351897b06db74602f1d5b097acd7e03425e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494240"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="45a96-102">Método ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="45a96-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="45a96-103">Obtém o número especificado de módulos contíguos de uma coleção sequencial de módulos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="45a96-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45a96-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45a96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45a96-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="45a96-106">[in] O número de módulos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="45a96-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="45a96-107">[out] Uma matriz de `ModuleID` valores, cada um deles representa um módulo recuperado.</span><span class="sxs-lookup"><span data-stu-id="45a96-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="45a96-108">[out] Um ponteiro para o número de elementos realmente retornados no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="45a96-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45a96-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="45a96-109">Return Value</span></span>  
 <span data-ttu-id="45a96-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="45a96-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="45a96-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45a96-111">HRESULT</span></span>|<span data-ttu-id="45a96-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="45a96-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45a96-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="45a96-113">S_OK</span></span>|<span data-ttu-id="45a96-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="45a96-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="45a96-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="45a96-115">S_FALSE</span></span>|<span data-ttu-id="45a96-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="45a96-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45a96-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45a96-117">Requirements</span></span>  
 <span data-ttu-id="45a96-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45a96-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45a96-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45a96-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45a96-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45a96-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45a96-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45a96-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a96-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45a96-122">See also</span></span>
- [<span data-ttu-id="45a96-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="45a96-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="45a96-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="45a96-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
