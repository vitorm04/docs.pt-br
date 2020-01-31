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
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861093"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="1f3e6-102">Método ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="1f3e6-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="1f3e6-103">Avança o cursor deste enumerador de sua posição atual para que o número especificado de elementos seja ignorado.</span><span class="sxs-lookup"><span data-stu-id="1f3e6-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f3e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f3e6-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f3e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f3e6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1f3e6-106">no O número de elementos a serem ignorados.</span><span class="sxs-lookup"><span data-stu-id="1f3e6-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f3e6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1f3e6-107">Remarks</span></span>  
 <span data-ttu-id="1f3e6-108">A nova posição do cursor deste enumerador é: (posição atual) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="1f3e6-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f3e6-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1f3e6-109">Requirements</span></span>  
 <span data-ttu-id="1f3e6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f3e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f3e6-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1f3e6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f3e6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f3e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f3e6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f3e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3e6-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="1f3e6-114">See also</span></span>

- [<span data-ttu-id="1f3e6-115">Interface ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1f3e6-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
