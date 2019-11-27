---
title: Método ICorProfilerFunctionEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 2ad4494cf3a429020099b4bd9d961341437fcd1e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447782"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="e2f58-102">Método ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="e2f58-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="e2f58-103">Obtém o número especificado de funções contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="e2f58-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2f58-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f58-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e2f58-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e2f58-106">no O número de funções a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="e2f58-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="e2f58-107">fora Uma matriz de valores de `COR_PRF_FUNCTION`, cada um representando uma função recuperada.</span><span class="sxs-lookup"><span data-stu-id="e2f58-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e2f58-108">fora Um ponteiro para o número de funções realmente retornadas na matriz de `ids`.</span><span class="sxs-lookup"><span data-stu-id="e2f58-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2f58-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e2f58-109">Return Value</span></span>  
 <span data-ttu-id="e2f58-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="e2f58-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2f58-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2f58-111">HRESULT</span></span>|<span data-ttu-id="e2f58-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2f58-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2f58-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2f58-113">S_OK</span></span>|<span data-ttu-id="e2f58-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="e2f58-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="e2f58-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e2f58-115">S_FALSE</span></span>|<span data-ttu-id="e2f58-116">Foram retornados menos de `celt` elementos, o que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="e2f58-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2f58-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2f58-117">Requirements</span></span>  
 <span data-ttu-id="e2f58-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f58-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f58-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e2f58-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2f58-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2f58-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2f58-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f58-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f58-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2f58-122">See also</span></span>

- [<span data-ttu-id="e2f58-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="e2f58-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="e2f58-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e2f58-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
