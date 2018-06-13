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
ms.openlocfilehash: 6c394690f6c8d7f3618b385b0a1432fc396fb819
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458014"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="414ba-102">Método ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="414ba-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="414ba-103">Retorna um enumerador que fornece métodos para sequencialmente iterar através da coleção de todos os threads gerenciados no processo com perfil.</span><span class="sxs-lookup"><span data-stu-id="414ba-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="414ba-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="414ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="414ba-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="414ba-106">[out] Um ponteiro para um [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="414ba-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="414ba-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="414ba-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414ba-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="414ba-108">Requirements</span></span>  
 <span data-ttu-id="414ba-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="414ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="414ba-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="414ba-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="414ba-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="414ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="414ba-112">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="414ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414ba-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="414ba-113">See Also</span></span>  
 [<span data-ttu-id="414ba-114">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="414ba-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="414ba-115">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="414ba-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="414ba-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="414ba-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="414ba-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="414ba-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
