---
title: "Enumeração COR_PRF_FINALIZER_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FINALIZER_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FINALIZER_FLAGS
helpviewer_keywords: COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 63707ca18be29555919264f9aa3a0f143efdd374
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="6dd6a-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6dd6a-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="6dd6a-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="6dd6a-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dd6a-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6dd6a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6dd6a-105">Members</span></span>  
  
|<span data-ttu-id="6dd6a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6dd6a-106">Member</span></span>|<span data-ttu-id="6dd6a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dd6a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="6dd6a-108">O finalizador é crítico.</span><span class="sxs-lookup"><span data-stu-id="6dd6a-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dd6a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6dd6a-109">Remarks</span></span>  
 <span data-ttu-id="6dd6a-110">O `COR_PRF_FINALIZER_FLAGS` enumeração é usada pelo [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) método para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="6dd6a-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd6a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6dd6a-111">Requirements</span></span>  
 <span data-ttu-id="6dd6a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dd6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dd6a-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dd6a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dd6a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dd6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dd6a-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd6a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dd6a-116">See Also</span></span>  
 [<span data-ttu-id="6dd6a-117">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6dd6a-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
