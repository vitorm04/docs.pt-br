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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9472013dcbbeef51753980348652b74c34172ce5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499206"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="7bf2b-102">Método ICorProfilerModuleEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="7bf2b-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="7bf2b-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos é ignorado.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bf2b-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bf2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bf2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7bf2b-106">[in] O número de elementos a serem ignoradas.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bf2b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7bf2b-107">Return Value</span></span>  
 <span data-ttu-id="7bf2b-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7bf2b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bf2b-109">HRESULT</span></span>|<span data-ttu-id="7bf2b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bf2b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bf2b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bf2b-111">S_OK</span></span>|<span data-ttu-id="7bf2b-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="7bf2b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7bf2b-113">S_FALSE</span></span>|<span data-ttu-id="7bf2b-114">Menos de `celt` elementos foram ignorados, que indica que não há mais nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bf2b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bf2b-115">Remarks</span></span>  
 <span data-ttu-id="7bf2b-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="7bf2b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf2b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bf2b-117">Requirements</span></span>  
 <span data-ttu-id="7bf2b-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf2b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf2b-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7bf2b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7bf2b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf2b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf2b-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf2b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf2b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bf2b-122">See also</span></span>
- [<span data-ttu-id="7bf2b-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="7bf2b-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="7bf2b-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7bf2b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
