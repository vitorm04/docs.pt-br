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
ms.openlocfilehash: fa85fb2cebb47ecbd7b0f091cb79f6ea0936b1cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598994"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="67898-102">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="67898-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="67898-103">Especifica quanto dados a serem passados de volta com um instantâneo de pilha em cada chamada para o criador de perfil [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="67898-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67898-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67898-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="67898-105">Membros</span><span class="sxs-lookup"><span data-stu-id="67898-105">Members</span></span>  
  
|<span data-ttu-id="67898-106">Membros</span><span class="sxs-lookup"><span data-stu-id="67898-106">Members</span></span>|<span data-ttu-id="67898-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="67898-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="67898-108">Indica que os valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, exceto o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="67898-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="67898-109">Indica que os valores devem ser passados para todos os `StackSnapshotCallback` parâmetros, incluindo o `context` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="67898-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="67898-110">Indica que um algoritmo de movimentação de pilha mais simples e alternativo será usado.</span><span class="sxs-lookup"><span data-stu-id="67898-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67898-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="67898-111">Remarks</span></span>  
 <span data-ttu-id="67898-112">Valores que são fornecidos pela `COR_PRF_SNAPSHOT_INFO` enumeração são passados como parâmetros para o [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="67898-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67898-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67898-113">Requirements</span></span>  
 <span data-ttu-id="67898-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67898-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67898-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67898-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67898-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67898-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67898-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67898-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67898-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67898-118">See also</span></span>

- [<span data-ttu-id="67898-119">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="67898-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="67898-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="67898-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
