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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbdb9f6fc8376e080455957367dc79f4dfed8843
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781206"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="5ff1d-102">Método ICorProfilerThreadEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="5ff1d-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="5ff1d-103">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff1d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ff1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff1d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ff1d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5ff1d-106">[out] O número de threads usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff1d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ff1d-107">Requirements</span></span>  
 <span data-ttu-id="5ff1d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff1d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff1d-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ff1d-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ff1d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ff1d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ff1d-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff1d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff1d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ff1d-112">See also</span></span>

- [<span data-ttu-id="5ff1d-113">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="5ff1d-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="5ff1d-114">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="5ff1d-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
