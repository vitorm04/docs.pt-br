---
title: Interface ICorProfilerAssemblyReferenceProvider
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 17fb3de830d1aed2214631bbe8254a7f58030025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500514"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="7060f-102">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="7060f-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="7060f-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="7060f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7060f-104">Permite que o criador de perfil informe o Common Language Runtime (CLR) de referências de assembly que o criador de perfil adicionará ao retorno de chamada [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7060f-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7060f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7060f-105">Methods</span></span>  
  
|<span data-ttu-id="7060f-106">Método</span><span class="sxs-lookup"><span data-stu-id="7060f-106">Method</span></span>|<span data-ttu-id="7060f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7060f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7060f-108">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="7060f-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="7060f-109">Informa o CLR de uma referência de assembly que o criador de perfil planeja adicionar ao retorno de chamada [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7060f-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7060f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7060f-110">Remarks</span></span>  
 <span data-ttu-id="7060f-111">O CLR passa o criador de perfil de um `ICorProfilerAssemblyReferenceProvider` objeto de interface no retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7060f-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="7060f-112">Isso permite que o criador de perfil informe o CLR de referências de assembly que o criador de perfil planeja adicionar posteriormente no [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="7060f-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="7060f-113">.</span><span class="sxs-lookup"><span data-stu-id="7060f-113">callback.</span></span> <span data-ttu-id="7060f-114">Isso melhora a precisão do caminhador de fechamento de referência do assembly do CLR e de seus algoritmos para determinar se os assemblies podem ser compartilhados.</span><span class="sxs-lookup"><span data-stu-id="7060f-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="7060f-115">Essa interface pode ser usada somente no retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) que passa esse objeto de interface para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="7060f-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7060f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7060f-116">Requirements</span></span>  
 <span data-ttu-id="7060f-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7060f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7060f-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7060f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7060f-119">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7060f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7060f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="7060f-120">See also</span></span>

- [<span data-ttu-id="7060f-121">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="7060f-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
