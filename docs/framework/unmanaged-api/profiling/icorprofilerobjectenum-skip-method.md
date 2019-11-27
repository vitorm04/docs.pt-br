---
title: Método ICorProfilerObjectEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 3c573c709e765fa723a726f5c8990ba59222ed1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428132"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="92627-102">Método ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="92627-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="92627-103">Avança o cursor deste enumerador de sua posição atual para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="92627-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92627-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92627-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92627-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92627-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="92627-106">no O número de elementos a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="92627-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92627-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="92627-107">Remarks</span></span>  
 <span data-ttu-id="92627-108">A nova posição do cursor deste enumerador é: (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="92627-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92627-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="92627-109">Requirements</span></span>  
 <span data-ttu-id="92627-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92627-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92627-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92627-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92627-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92627-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92627-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92627-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92627-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92627-114">See also</span></span>

- [<span data-ttu-id="92627-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="92627-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
