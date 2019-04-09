---
title: Método ICorProfilerInfo4::EnumThreads
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd0a4149b6dc6023579e8bc5b40751d23416e3a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202359"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="45e07-102">Método ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="45e07-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="45e07-103">Retorna um enumerador que fornece métodos para iterar de forma sequencial por meio da coleção de todos os threads gerenciados no processo de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="45e07-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45e07-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45e07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45e07-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="45e07-106">[out] Um ponteiro para um [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="45e07-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e07-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="45e07-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e07-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45e07-108">Requirements</span></span>  
 <span data-ttu-id="45e07-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e07-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45e07-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45e07-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45e07-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="45e07-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="45e07-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45e07-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45e07-113">See also</span></span>

- [<span data-ttu-id="45e07-114">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="45e07-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="45e07-115">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="45e07-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="45e07-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="45e07-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="45e07-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="45e07-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
