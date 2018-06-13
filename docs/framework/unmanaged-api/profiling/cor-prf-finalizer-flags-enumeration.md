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
ms.openlocfilehash: 9292e7c5908b2e4fd7e2c0ae9412375249f2fdfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449940"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="60ef3-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="60ef3-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="60ef3-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="60ef3-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ef3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60ef3-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="60ef3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="60ef3-105">Members</span></span>  
  
|<span data-ttu-id="60ef3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="60ef3-106">Member</span></span>|<span data-ttu-id="60ef3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="60ef3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="60ef3-108">O finalizador é crítico.</span><span class="sxs-lookup"><span data-stu-id="60ef3-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ef3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="60ef3-109">Remarks</span></span>  
 <span data-ttu-id="60ef3-110">O `COR_PRF_FINALIZER_FLAGS` enumeração é usada pelo [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) método para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="60ef3-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60ef3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60ef3-111">Requirements</span></span>  
 <span data-ttu-id="60ef3-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60ef3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60ef3-113">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60ef3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60ef3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60ef3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60ef3-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60ef3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ef3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60ef3-116">See Also</span></span>  
 [<span data-ttu-id="60ef3-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="60ef3-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
