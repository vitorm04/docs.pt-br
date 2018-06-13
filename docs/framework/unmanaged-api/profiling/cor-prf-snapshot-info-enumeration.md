---
title: Enumeração COR_PRF_SNAPSHOT_INFO
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450711"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="1d729-102">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="1d729-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="1d729-103">Especifica o quanto os dados a serem passados novamente com um instantâneo de pilha em cada chamada para o criador de perfil [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="1d729-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d729-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1d729-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1d729-105">Members</span></span>  
  
|<span data-ttu-id="1d729-106">Membros</span><span class="sxs-lookup"><span data-stu-id="1d729-106">Members</span></span>|<span data-ttu-id="1d729-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d729-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="1d729-108">Indica que valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, exceto o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d729-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="1d729-109">Indica que valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, incluindo o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1d729-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="1d729-110">Indica que um algoritmo de movimentação de pilha mais simples e alternativo será usado.</span><span class="sxs-lookup"><span data-stu-id="1d729-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d729-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d729-111">Remarks</span></span>  
 <span data-ttu-id="1d729-112">Valores que são fornecidos pelo `COR_PRF_SNAPSHOT_INFO` enumeração são passados como parâmetros para o [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1d729-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d729-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d729-113">Requirements</span></span>  
 <span data-ttu-id="1d729-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d729-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d729-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d729-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d729-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d729-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d729-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d729-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d729-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d729-118">See Also</span></span>  
 [<span data-ttu-id="1d729-119">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="1d729-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="1d729-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="1d729-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
