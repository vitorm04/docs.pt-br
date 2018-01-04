---
title: "Método ICorProfilerFunctionEnum::Skip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddde6069072092cfc0441686ce4d53aa0a4bd534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="8e3c2-102">Método ICorProfilerFunctionEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="8e3c2-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="8e3c2-103">Avança o cursor do enumerador de sua posição atual para que o número especificado de elementos será ignorado.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e3c2-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e3c2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e3c2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8e3c2-106">[in] O número de elementos seja ignorada.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e3c2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e3c2-107">Return Value</span></span>  
 <span data-ttu-id="8e3c2-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8e3c2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e3c2-109">HRESULT</span></span>|<span data-ttu-id="8e3c2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e3c2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e3c2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e3c2-111">S_OK</span></span>|<span data-ttu-id="8e3c2-112">`celt`elementos foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="8e3c2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8e3c2-113">S_FALSE</span></span>|<span data-ttu-id="8e3c2-114">Menos de `celt` elementos foram ignorados, que indica que não existem mais elementos.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e3c2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e3c2-115">Remarks</span></span>  
 <span data-ttu-id="8e3c2-116">A nova posição do cursor deste enumerador é (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="8e3c2-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e3c2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e3c2-117">Requirements</span></span>  
 <span data-ttu-id="8e3c2-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e3c2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e3c2-119">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e3c2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e3c2-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e3c2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e3c2-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e3c2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3c2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e3c2-122">See Also</span></span>  
 [<span data-ttu-id="8e3c2-123">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="8e3c2-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="8e3c2-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8e3c2-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
