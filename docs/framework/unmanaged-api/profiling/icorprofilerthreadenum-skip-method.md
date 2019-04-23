---
title: Método ICorProfilerThreadEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cce96e8c6d046beba9e45c7121bf68444fd51c95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173336"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="eaa1d-102">Método ICorProfilerThreadEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="eaa1d-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="eaa1d-103">Avança o cursor do enumerador de sua posição atual para ignorar o número especificado de elementos.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eaa1d-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eaa1d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="eaa1d-106">[in] O número de elementos a serem ignoradas.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaa1d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="eaa1d-107">Return Value</span></span>  
 <span data-ttu-id="eaa1d-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eaa1d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaa1d-109">HRESULT</span></span>|<span data-ttu-id="eaa1d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="eaa1d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaa1d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaa1d-111">S_OK</span></span>|<span data-ttu-id="eaa1d-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="eaa1d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="eaa1d-113">S_FALSE</span></span>|<span data-ttu-id="eaa1d-114">Menos de `celt` elementos foram ignorados, que indica que não há mais nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa1d-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="eaa1d-115">Remarks</span></span>  
 <span data-ttu-id="eaa1d-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="eaa1d-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa1d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eaa1d-117">Requirements</span></span>  
 <span data-ttu-id="eaa1d-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa1d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa1d-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eaa1d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaa1d-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaa1d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaa1d-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa1d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa1d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaa1d-122">See also</span></span>

- [<span data-ttu-id="eaa1d-123">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="eaa1d-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="eaa1d-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="eaa1d-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
