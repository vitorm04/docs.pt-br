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
ms.openlocfilehash: d5037f335e8d66c341d70d91d955a1ac7571b823
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775135"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="c25d4-102">Enumeração COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c25d4-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="c25d4-103">Descreve o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="c25d4-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c25d4-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c25d4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c25d4-105">Members</span></span>  
  
|<span data-ttu-id="c25d4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c25d4-106">Member</span></span>|<span data-ttu-id="c25d4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c25d4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="c25d4-108">O finalizador é essencial.</span><span class="sxs-lookup"><span data-stu-id="c25d4-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c25d4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c25d4-109">Remarks</span></span>  
 <span data-ttu-id="c25d4-110">O `COR_PRF_FINALIZER_FLAGS` enumeração é usada pelo [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) método para descrever o finalizador de um objeto.</span><span class="sxs-lookup"><span data-stu-id="c25d4-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c25d4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c25d4-111">Requirements</span></span>  
 <span data-ttu-id="c25d4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25d4-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c25d4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c25d4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c25d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c25d4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c25d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25d4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c25d4-116">See also</span></span>

- [<span data-ttu-id="c25d4-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="c25d4-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
