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
ms.openlocfilehash: 361f08f8c787ad4c1288c56fb1bdb4d5136933e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442694"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="ca255-102">Método ICorProfilerModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="ca255-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="ca255-103">Obtém o número especificado de módulos contíguos de uma coleção sequencial de módulos, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="ca255-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca255-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca255-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca255-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca255-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ca255-106">no O número de módulos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="ca255-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="ca255-107">fora Uma matriz de valores de `ModuleID`, cada um representando um módulo recuperado.</span><span class="sxs-lookup"><span data-stu-id="ca255-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ca255-108">fora Um ponteiro para o número de elementos realmente retornados na matriz de `ids`.</span><span class="sxs-lookup"><span data-stu-id="ca255-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca255-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ca255-109">Return Value</span></span>  
 <span data-ttu-id="ca255-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="ca255-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ca255-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca255-111">HRESULT</span></span>|<span data-ttu-id="ca255-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca255-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca255-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca255-113">S_OK</span></span>|<span data-ttu-id="ca255-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="ca255-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="ca255-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ca255-115">S_FALSE</span></span>|<span data-ttu-id="ca255-116">Foram retornados menos de `celt` elementos, o que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="ca255-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca255-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ca255-117">Requirements</span></span>  
 <span data-ttu-id="ca255-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca255-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca255-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ca255-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca255-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca255-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca255-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca255-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca255-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca255-122">See also</span></span>

- [<span data-ttu-id="ca255-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="ca255-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="ca255-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ca255-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
