---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175064"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="fcc45-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="fcc45-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="fcc45-103">Uma subclasse do [ICorProfilerInfo9](icorprofilerinfo9-interface.md) que fornece métodos para modificar a função IL, consultar informações a partir do tempo de execução e suspender e retomar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fcc45-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="fcc45-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fcc45-104">Methods</span></span>  

| <span data-ttu-id="fcc45-105">Método</span><span class="sxs-lookup"><span data-stu-id="fcc45-105">Method</span></span>|<span data-ttu-id="fcc45-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcc45-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="fcc45-107">Método EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="fcc45-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="fcc45-108">Dado um ObjectID, callback e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="fcc45-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="fcc45-109">Método IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="fcc45-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="fcc45-110">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="fcc45-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="fcc45-111">Método GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="fcc45-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="fcc45-112">Obtém o valor do limite LOH configurado.</span><span class="sxs-lookup"><span data-stu-id="fcc45-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="fcc45-113">Método RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="fcc45-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="fcc45-114">ReJITs os métodos solicitados, bem como quaisquer inliners dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="fcc45-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="fcc45-115">Método SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="fcc45-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="fcc45-116">Suspende o tempo de execução sem realizar um GC.</span><span class="sxs-lookup"><span data-stu-id="fcc45-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="fcc45-117">Método ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="fcc45-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="fcc45-118">Retoma o tempo de execução sem realizar um GC.</span><span class="sxs-lookup"><span data-stu-id="fcc45-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="fcc45-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc45-119">Requirements</span></span>  
<span data-ttu-id="fcc45-120">**Plataformas:** Consulte [os sistemas operacionais suportados pelo .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="fcc45-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="fcc45-121">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fcc45-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="fcc45-122">**.NET Versões:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc45-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc45-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="fcc45-123">See also</span></span>

- [<span data-ttu-id="fcc45-124">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="fcc45-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
