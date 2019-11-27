---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449835"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="b1977-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="b1977-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="b1977-103">Uma subclasse de [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) que fornece métodos para modificar o Il da função, consultar informações do tempo de execução e suspender e retomar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b1977-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="b1977-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b1977-104">Methods</span></span>  

| <span data-ttu-id="b1977-105">Método</span><span class="sxs-lookup"><span data-stu-id="b1977-105">Method</span></span>|<span data-ttu-id="b1977-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1977-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="b1977-107">Método EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="b1977-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="b1977-108">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="b1977-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="b1977-109">Método iscongeladoobject</span><span class="sxs-lookup"><span data-stu-id="b1977-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="b1977-110">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="b1977-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="b1977-111">Método GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="b1977-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="b1977-112">Obtém o valor do limite de LOH configurado.</span><span class="sxs-lookup"><span data-stu-id="b1977-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="b1977-113">Método RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="b1977-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="b1977-114">ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="b1977-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="b1977-115">Método SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="b1977-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="b1977-116">Suspende o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="b1977-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="b1977-117">Método ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="b1977-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="b1977-118">Retoma o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="b1977-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="b1977-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1977-119">Requirements</span></span>  
<span data-ttu-id="b1977-120">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b1977-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="b1977-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1977-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="b1977-122">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1977-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="b1977-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1977-123">See also</span></span>

- [<span data-ttu-id="b1977-124">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b1977-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
