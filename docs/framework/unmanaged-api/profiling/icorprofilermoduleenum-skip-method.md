---
title: Método ICorProfilerModuleEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: d8c0f69ce407638aed6475c4d84d0e032cc6a8f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435983"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="5591a-102">Método ICorProfilerModuleEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="5591a-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="5591a-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="5591a-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5591a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5591a-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5591a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5591a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5591a-106">no O número de elementos a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="5591a-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5591a-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5591a-107">Return Value</span></span>  
 <span data-ttu-id="5591a-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="5591a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5591a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5591a-109">HRESULT</span></span>|<span data-ttu-id="5591a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5591a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5591a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5591a-111">S_OK</span></span>|<span data-ttu-id="5591a-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="5591a-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="5591a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5591a-113">S_FALSE</span></span>|<span data-ttu-id="5591a-114">Menos de `celt` elementos foram ignorados, o que indica que não há mais elementos.</span><span class="sxs-lookup"><span data-stu-id="5591a-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5591a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5591a-115">Remarks</span></span>  
 <span data-ttu-id="5591a-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="5591a-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5591a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5591a-117">Requirements</span></span>  
 <span data-ttu-id="5591a-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5591a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5591a-119">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5591a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5591a-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5591a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5591a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5591a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5591a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5591a-122">See also</span></span>

- [<span data-ttu-id="5591a-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="5591a-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="5591a-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5591a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
