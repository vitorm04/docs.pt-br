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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bcc837fede7e7db59bdf88a0b5434a7c1924335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210939"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="e6043-102">Método ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="e6043-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="e6043-103">Avança o cursor este enumerador de sua posição atual para que o número especificado de elementos é ignorado.</span><span class="sxs-lookup"><span data-stu-id="e6043-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6043-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6043-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6043-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6043-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e6043-106">[in] O número de elementos a serem ignoradas.</span><span class="sxs-lookup"><span data-stu-id="e6043-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6043-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6043-107">Remarks</span></span>  
 <span data-ttu-id="e6043-108">A nova posição do cursor deste enumerador é: (posição atual) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="e6043-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6043-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6043-109">Requirements</span></span>  
 <span data-ttu-id="e6043-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6043-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6043-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6043-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6043-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6043-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6043-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6043-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6043-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6043-114">See also</span></span>

- [<span data-ttu-id="e6043-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="e6043-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
