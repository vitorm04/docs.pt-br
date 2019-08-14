---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974006"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="6af4c-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="6af4c-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="6af4c-103">Uma subclasse de [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) que fornece métodos para modificar o Il da função, consultar informações do tempo de execução e suspender e retomar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6af4c-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="6af4c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6af4c-104">Methods</span></span>  

| <span data-ttu-id="6af4c-105">Método</span><span class="sxs-lookup"><span data-stu-id="6af4c-105">Method</span></span>|<span data-ttu-id="6af4c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6af4c-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="6af4c-107">Método EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="6af4c-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="6af4c-108">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="6af4c-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="6af4c-109">Método iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="6af4c-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="6af4c-110">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6af4c-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="6af4c-111">Método GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="6af4c-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="6af4c-112">Obtém o valor do limite de LOH configurado.</span><span class="sxs-lookup"><span data-stu-id="6af4c-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="6af4c-113">Método RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="6af4c-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="6af4c-114">ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="6af4c-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="6af4c-115">Método SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="6af4c-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="6af4c-116">Suspende o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="6af4c-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="6af4c-117">Método ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="6af4c-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="6af4c-118">Retoma o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="6af4c-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6af4c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6af4c-119">Requirements</span></span>  
<span data-ttu-id="6af4c-120">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="6af4c-120">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="6af4c-121">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6af4c-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="6af4c-122">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af4c-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
## <a name="see-also"></a><span data-ttu-id="6af4c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6af4c-123">See also</span></span>
- [<span data-ttu-id="6af4c-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6af4c-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
