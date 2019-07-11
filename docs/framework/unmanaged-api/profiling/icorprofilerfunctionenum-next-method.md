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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d51f26e6d3fa2c37e1588d255f04578dce5bc24
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780297"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="b50a8-102">Método ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="b50a8-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="b50a8-103">Obtém o número especificado de funções contíguos de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="b50a8-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b50a8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b50a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b50a8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b50a8-106">[in] O número de funções para recuperar.</span><span class="sxs-lookup"><span data-stu-id="b50a8-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="b50a8-107">[out] Uma matriz de `COR_PRF_FUNCTION` valores, cada um deles representa uma função recuperada.</span><span class="sxs-lookup"><span data-stu-id="b50a8-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b50a8-108">[out] Um ponteiro para o número de funções, na verdade, é retornado no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="b50a8-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b50a8-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b50a8-109">Return Value</span></span>  
 <span data-ttu-id="b50a8-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="b50a8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b50a8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b50a8-111">HRESULT</span></span>|<span data-ttu-id="b50a8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b50a8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b50a8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b50a8-113">S_OK</span></span>|<span data-ttu-id="b50a8-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="b50a8-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="b50a8-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b50a8-115">S_FALSE</span></span>|<span data-ttu-id="b50a8-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="b50a8-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b50a8-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50a8-117">Requirements</span></span>  
 <span data-ttu-id="b50a8-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b50a8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b50a8-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b50a8-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b50a8-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b50a8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b50a8-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b50a8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50a8-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b50a8-122">See also</span></span>

- [<span data-ttu-id="b50a8-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="b50a8-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="b50a8-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b50a8-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
