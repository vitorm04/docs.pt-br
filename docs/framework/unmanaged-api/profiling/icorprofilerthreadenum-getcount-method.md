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
ms.openlocfilehash: 8b02f70f22a7d35bf0fe7816a52c490f88b31217
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218427"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="c0c3e-102">Método ICorProfilerThreadEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="c0c3e-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="c0c3e-103">Obtém o número de threads que são usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0c3e-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0c3e-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0c3e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c0c3e-106">[out] O número de threads usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0c3e-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c3e-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0c3e-107">Requirements</span></span>  
 <span data-ttu-id="c0c3e-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0c3e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c3e-109">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0c3e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0c3e-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0c3e-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c0c3e-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c0c3e-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0c3e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0c3e-112">See also</span></span>

- [<span data-ttu-id="c0c3e-113">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="c0c3e-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="c0c3e-114">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="c0c3e-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
