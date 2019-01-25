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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65c18f534771407b2dcf4710e2604e0b30cbdcdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611040"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="31826-102">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="31826-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="31826-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="31826-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="31826-104">Permite que o criador de perfil informar o common language runtime (CLR) de referências de assembly que o criador de perfil será adicionado a [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="31826-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31826-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="31826-105">Methods</span></span>  
  
|<span data-ttu-id="31826-106">Método</span><span class="sxs-lookup"><span data-stu-id="31826-106">Method</span></span>|<span data-ttu-id="31826-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31826-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31826-108">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="31826-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="31826-109">Informa ao CLR uma referência de assembly que o criador de perfil planeja adicionar à [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="31826-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31826-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="31826-110">Remarks</span></span>  
 <span data-ttu-id="31826-111">O CLR passa o criador de perfil uma `ICorProfilerAssemblyReferenceProvider` objeto de interface na [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="31826-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="31826-112">Isso permite que o criador de perfil informe ao CLR de referências de assembly que o criador de perfil planeja adicionar mais tarde a [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="31826-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="31826-113">.</span><span class="sxs-lookup"><span data-stu-id="31826-113">callback.</span></span> <span data-ttu-id="31826-114">Isso melhora a precisão do caminhador de fechamento de referência do assembly do CLR e de seus algoritmos para determinar se os assemblies podem ser compartilhados.</span><span class="sxs-lookup"><span data-stu-id="31826-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="31826-115">Essa interface pode ser usada somente na [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada que passa esse objeto de interface para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="31826-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31826-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31826-116">Requirements</span></span>  
 <span data-ttu-id="31826-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31826-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31826-118">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31826-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31826-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31826-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31826-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31826-120">See also</span></span>
- [<span data-ttu-id="31826-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="31826-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
