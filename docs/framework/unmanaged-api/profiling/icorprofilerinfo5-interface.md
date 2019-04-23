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
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094249"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="7ab84-102">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="7ab84-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="7ab84-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="7ab84-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7ab84-104">Uma subclasse de [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) que fornece métodos para uso por criadores de perfil de código para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="7ab84-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ab84-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7ab84-105">Methods</span></span>  
  
|<span data-ttu-id="7ab84-106">Método</span><span class="sxs-lookup"><span data-stu-id="7ab84-106">Method</span></span>|<span data-ttu-id="7ab84-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ab84-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ab84-108">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="7ab84-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="7ab84-109">Obtém as categorias de eventos atuais para os quais o criador de perfis deseja receber notificações do CLR.</span><span class="sxs-lookup"><span data-stu-id="7ab84-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="7ab84-110">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="7ab84-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="7ab84-111">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR.</span><span class="sxs-lookup"><span data-stu-id="7ab84-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ab84-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ab84-112">Remarks</span></span>  
 <span data-ttu-id="7ab84-113">Os métodos disponíveis nessa interface são destinados a substituir a [ICorProfilerInfo:: Geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="7ab84-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab84-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ab84-114">Requirements</span></span>  
 <span data-ttu-id="7ab84-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab84-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ab84-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ab84-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab84-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab84-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ab84-118">See also</span></span>

- [<span data-ttu-id="7ab84-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7ab84-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
