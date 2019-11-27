---
title: Método ICorProfilerThreadEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 695b720119854de4645b2f14dd55811f2465504a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447647"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="1439a-102">Método ICorProfilerThreadEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="1439a-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="1439a-103">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1439a-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1439a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1439a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1439a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1439a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1439a-106">fora O número de threads usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1439a-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1439a-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1439a-107">Requirements</span></span>  
 <span data-ttu-id="1439a-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1439a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1439a-109">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1439a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1439a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1439a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1439a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1439a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1439a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1439a-112">See also</span></span>

- [<span data-ttu-id="1439a-113">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="1439a-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="1439a-114">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1439a-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
