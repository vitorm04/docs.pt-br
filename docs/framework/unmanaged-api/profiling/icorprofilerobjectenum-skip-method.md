---
title: "Método ICorProfilerObjectEnum::Skip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84960af6e128f3a6aa9e3b45187e282ac7228e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="fe6a6-102">Método ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="fe6a6-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="fe6a6-103">Avança o cursor deste enumerador de sua posição atual para que o número especificado de elementos será ignorado.</span><span class="sxs-lookup"><span data-stu-id="fe6a6-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe6a6-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe6a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe6a6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fe6a6-106">[in] O número de elementos seja ignorada.</span><span class="sxs-lookup"><span data-stu-id="fe6a6-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe6a6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe6a6-107">Remarks</span></span>  
 <span data-ttu-id="fe6a6-108">A nova posição do cursor deste enumerador é: (posição atual) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="fe6a6-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6a6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe6a6-109">Requirements</span></span>  
 <span data-ttu-id="fe6a6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe6a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe6a6-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe6a6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe6a6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe6a6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe6a6-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe6a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6a6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe6a6-114">See Also</span></span>  
 [<span data-ttu-id="fe6a6-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="fe6a6-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
