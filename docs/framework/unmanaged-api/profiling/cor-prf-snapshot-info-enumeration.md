---
title: "Enumeração COR_PRF_SNAPSHOT_INFO"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4573ec44253b1b0f26ae62591db149f0447d3935
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="1565f-102">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="1565f-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="1565f-103">Especifica o quanto os dados a serem passados novamente com um instantâneo de pilha em cada chamada para o criador de perfil [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="1565f-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1565f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1565f-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1565f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1565f-105">Members</span></span>  
  
|<span data-ttu-id="1565f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="1565f-106">Members</span></span>|<span data-ttu-id="1565f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1565f-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="1565f-108">Indica que valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, exceto o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1565f-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="1565f-109">Indica que valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, incluindo o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1565f-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="1565f-110">Indica que um algoritmo de movimentação de pilha mais simples e alternativo será usado.</span><span class="sxs-lookup"><span data-stu-id="1565f-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1565f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1565f-111">Remarks</span></span>  
 <span data-ttu-id="1565f-112">Valores que são fornecidos pelo `COR_PRF_SNAPSHOT_INFO` enumeração são passados como parâmetros para o [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1565f-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1565f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1565f-113">Requirements</span></span>  
 <span data-ttu-id="1565f-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1565f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1565f-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1565f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1565f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1565f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1565f-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1565f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1565f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1565f-118">See Also</span></span>  
 [<span data-ttu-id="1565f-119">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="1565f-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="1565f-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="1565f-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
