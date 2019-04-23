---
title: Enumeração COR_PRF_GC_ROOT_KIND
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfbba3cef8afadfc6e12e53ea328c4fc7165ca0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206753"
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="66a7d-102">Enumeração COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="66a7d-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="66a7d-103">Indica o tipo de raiz de coleta de lixo é exposto pelo [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="66a7d-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66a7d-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="66a7d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="66a7d-105">Members</span></span>  
  
|<span data-ttu-id="66a7d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="66a7d-106">Member</span></span>|<span data-ttu-id="66a7d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="66a7d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="66a7d-108">A raiz é uma variável na pilha.</span><span class="sxs-lookup"><span data-stu-id="66a7d-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="66a7d-109">A raiz é uma entrada na fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="66a7d-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="66a7d-110">A raiz é um identificador da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="66a7d-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="66a7d-111">O tipo de raiz não está especificado.</span><span class="sxs-lookup"><span data-stu-id="66a7d-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66a7d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66a7d-112">Requirements</span></span>  
 <span data-ttu-id="66a7d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a7d-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66a7d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66a7d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a7d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a7d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a7d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66a7d-117">See also</span></span>

- [<span data-ttu-id="66a7d-118">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="66a7d-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
