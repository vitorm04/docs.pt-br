---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 7e483bae9b7898e25c376fa92d0449fc49c6f9ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548677"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="3785e-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="3785e-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="3785e-103">Uma subclasse de [ICorProfilerInfo9](icorprofilerinfo9-interface.md) que fornece métodos para modificar o Il da função, consultar informações do tempo de execução e suspender e retomar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3785e-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="3785e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3785e-104">Methods</span></span>  

| <span data-ttu-id="3785e-105">Método</span><span class="sxs-lookup"><span data-stu-id="3785e-105">Method</span></span>|<span data-ttu-id="3785e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3785e-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="3785e-107">Método EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="3785e-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="3785e-108">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="3785e-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="3785e-109">Método IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="3785e-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="3785e-110">Dado um ObjectID, determina se o objeto está em um segmento somente leitura.</span><span class="sxs-lookup"><span data-stu-id="3785e-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="3785e-111">Método GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="3785e-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="3785e-112">Obtém o valor do limite de LOH configurado.</span><span class="sxs-lookup"><span data-stu-id="3785e-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="3785e-113">Método RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="3785e-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="3785e-114">ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="3785e-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="3785e-115">Método SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="3785e-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="3785e-116">Suspende o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="3785e-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="3785e-117">Método ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="3785e-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="3785e-118">Retoma o tempo de execução sem executar um GC.</span><span class="sxs-lookup"><span data-stu-id="3785e-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3785e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3785e-119">Requirements</span></span>  
<span data-ttu-id="3785e-120">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="3785e-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="3785e-121">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3785e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="3785e-122">**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3785e-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3785e-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="3785e-123">See also</span></span>

- [<span data-ttu-id="3785e-124">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="3785e-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
