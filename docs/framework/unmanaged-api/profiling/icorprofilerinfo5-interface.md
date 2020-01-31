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
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861717"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="fba7a-102">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="fba7a-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="fba7a-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="fba7a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fba7a-104">Uma subclasse de [ICorProfilerInfo4](icorprofilerinfo4-interface.md) que fornece métodos para uso por infilers de código para se comunicar com o Common Language Runtime (CLR) para controlar o monitoramento de eventos.</span><span class="sxs-lookup"><span data-stu-id="fba7a-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fba7a-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fba7a-105">Methods</span></span>  
  
|<span data-ttu-id="fba7a-106">Método</span><span class="sxs-lookup"><span data-stu-id="fba7a-106">Method</span></span>|<span data-ttu-id="fba7a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fba7a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fba7a-108">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="fba7a-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="fba7a-109">Obtém as categorias de eventos atuais para os quais o criador de perfis deseja receber notificações do CLR.</span><span class="sxs-lookup"><span data-stu-id="fba7a-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="fba7a-110">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="fba7a-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="fba7a-111">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR.</span><span class="sxs-lookup"><span data-stu-id="fba7a-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fba7a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fba7a-112">Remarks</span></span>  
 <span data-ttu-id="fba7a-113">Os métodos disponíveis nesta interface destinam-se a substituir os métodos [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fba7a-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fba7a-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fba7a-114">Requirements</span></span>  
 <span data-ttu-id="fba7a-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fba7a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fba7a-116">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fba7a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fba7a-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fba7a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba7a-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="fba7a-118">See also</span></span>

- [<span data-ttu-id="fba7a-119">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="fba7a-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
