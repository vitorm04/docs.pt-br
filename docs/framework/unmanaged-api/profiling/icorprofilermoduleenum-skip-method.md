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
ms.openlocfilehash: 35256a25ed793ffee6ddc1b26088e0988fea5af2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454332"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="ebe72-102">Método ICorProfilerModuleEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="ebe72-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="ebe72-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos será ignorado.</span><span class="sxs-lookup"><span data-stu-id="ebe72-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebe72-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebe72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ebe72-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ebe72-106">[in] O número de elementos seja ignorada.</span><span class="sxs-lookup"><span data-stu-id="ebe72-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebe72-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ebe72-107">Return Value</span></span>  
 <span data-ttu-id="ebe72-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="ebe72-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ebe72-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ebe72-109">HRESULT</span></span>|<span data-ttu-id="ebe72-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebe72-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ebe72-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ebe72-111">S_OK</span></span>|<span data-ttu-id="ebe72-112">`celt` elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="ebe72-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="ebe72-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ebe72-113">S_FALSE</span></span>|<span data-ttu-id="ebe72-114">Menos de `celt` elementos foram ignorados, que indica que não existem mais elementos.</span><span class="sxs-lookup"><span data-stu-id="ebe72-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebe72-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebe72-115">Remarks</span></span>  
 <span data-ttu-id="ebe72-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="ebe72-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe72-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ebe72-117">Requirements</span></span>  
 <span data-ttu-id="ebe72-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebe72-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebe72-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebe72-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebe72-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebe72-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebe72-121">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebe72-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe72-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebe72-122">See Also</span></span>  
 [<span data-ttu-id="ebe72-123">Interface ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="ebe72-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="ebe72-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ebe72-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
