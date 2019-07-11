---
title: Enumeração COR_PRF_FINALIZER_FLAGS
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a66b2b94765c3d59327e500f1e208dc93cd8e231
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781929"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="e295a-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e295a-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="e295a-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="e295a-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e295a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e295a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e295a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e295a-105">Members</span></span>  
  
|<span data-ttu-id="e295a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e295a-106">Member</span></span>|<span data-ttu-id="e295a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e295a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="e295a-108">O finalizador é essencial.</span><span class="sxs-lookup"><span data-stu-id="e295a-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e295a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e295a-109">Remarks</span></span>  
 <span data-ttu-id="e295a-110">O `COR_PRF_FINALIZER_FLAGS` enumeração é usada pelo [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) método para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="e295a-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e295a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e295a-111">Requirements</span></span>  
 <span data-ttu-id="e295a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e295a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e295a-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e295a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e295a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e295a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e295a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e295a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e295a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e295a-116">See also</span></span>

- [<span data-ttu-id="e295a-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="e295a-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
