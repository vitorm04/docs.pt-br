---
title: Interface ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ba082182ec7e2f639ef94baeb29203ee792fba0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="991c8-102">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="991c8-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="991c8-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="991c8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="991c8-104">Uma subclasse de [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) que fornece métodos para uso por criadores de perfil de código para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="991c8-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="991c8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="991c8-105">Methods</span></span>  
  
|<span data-ttu-id="991c8-106">Método</span><span class="sxs-lookup"><span data-stu-id="991c8-106">Method</span></span>|<span data-ttu-id="991c8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="991c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="991c8-108">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="991c8-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="991c8-109">Obtém as categorias de eventos atuais para os quais o criador de perfis deseja receber notificações do CLR.</span><span class="sxs-lookup"><span data-stu-id="991c8-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="991c8-110">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="991c8-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="991c8-111">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR.</span><span class="sxs-lookup"><span data-stu-id="991c8-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="991c8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="991c8-112">Remarks</span></span>  
 <span data-ttu-id="991c8-113">Os métodos disponíveis nesta interface destinam-se para substituir o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) e [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="991c8-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991c8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="991c8-114">Requirements</span></span>  
 <span data-ttu-id="991c8-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991c8-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="991c8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="991c8-117">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991c8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="991c8-118">See Also</span></span>  
 [<span data-ttu-id="991c8-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="991c8-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
