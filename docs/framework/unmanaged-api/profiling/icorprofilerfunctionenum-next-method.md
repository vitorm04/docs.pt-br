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
ms.openlocfilehash: 62e70a2fe421651aac9a4921ca885c53c864c4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991946"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="f161e-102">Método ICorProfilerFunctionEnum::Next</span><span class="sxs-lookup"><span data-stu-id="f161e-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="f161e-103">Obtém o número especificado de funções contíguos de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.</span><span class="sxs-lookup"><span data-stu-id="f161e-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f161e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f161e-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f161e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f161e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f161e-106">[in] O número de funções para recuperar.</span><span class="sxs-lookup"><span data-stu-id="f161e-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="f161e-107">[out] Uma matriz de `COR_PRF_FUNCTION` valores, cada um deles representa uma função recuperada.</span><span class="sxs-lookup"><span data-stu-id="f161e-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f161e-108">[out] Um ponteiro para o número de funções, na verdade, é retornado no `ids` matriz.</span><span class="sxs-lookup"><span data-stu-id="f161e-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f161e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f161e-109">Return Value</span></span>  
 <span data-ttu-id="f161e-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="f161e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f161e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f161e-111">HRESULT</span></span>|<span data-ttu-id="f161e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f161e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f161e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f161e-113">S_OK</span></span>|<span data-ttu-id="f161e-114">`celt` elementos foram retornados.</span><span class="sxs-lookup"><span data-stu-id="f161e-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="f161e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f161e-115">S_FALSE</span></span>|<span data-ttu-id="f161e-116">Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f161e-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f161e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f161e-117">Requirements</span></span>  
 <span data-ttu-id="f161e-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f161e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f161e-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f161e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f161e-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f161e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f161e-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f161e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f161e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f161e-122">See also</span></span>

- [<span data-ttu-id="f161e-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="f161e-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f161e-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f161e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
