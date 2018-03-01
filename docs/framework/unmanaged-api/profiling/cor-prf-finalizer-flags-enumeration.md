---
title: "Enumeração COR_PRF_FINALIZER_FLAGS"
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
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae0941e962b2fc1b08f0defb692038bd5fcf885a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="d4b59-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="d4b59-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="d4b59-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d4b59-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4b59-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="d4b59-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d4b59-105">Members</span></span>  
  
|<span data-ttu-id="d4b59-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d4b59-106">Member</span></span>|<span data-ttu-id="d4b59-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4b59-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="d4b59-108">O finalizador é crítico.</span><span class="sxs-lookup"><span data-stu-id="d4b59-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b59-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4b59-109">Remarks</span></span>  
 <span data-ttu-id="d4b59-110">O `COR_PRF_FINALIZER_FLAGS` enumeração é usada pelo [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) método para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d4b59-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b59-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4b59-111">Requirements</span></span>  
 <span data-ttu-id="d4b59-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b59-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b59-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4b59-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4b59-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4b59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4b59-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b59-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4b59-116">See Also</span></span>  
 [<span data-ttu-id="d4b59-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="d4b59-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
