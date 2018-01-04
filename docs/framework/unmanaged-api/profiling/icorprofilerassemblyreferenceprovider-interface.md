---
title: Interface ICorProfilerAssemblyReferenceProvider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 203362d2780d372236b05f753bedc0d59565d2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="54996-102">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="54996-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="54996-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="54996-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="54996-104">Permite que o criador de perfil informar o common language runtime (CLR) de referências de assembly que adicionará o criador de perfil de [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="54996-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54996-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="54996-105">Methods</span></span>  
  
|<span data-ttu-id="54996-106">Método</span><span class="sxs-lookup"><span data-stu-id="54996-106">Method</span></span>|<span data-ttu-id="54996-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="54996-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54996-108">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="54996-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="54996-109">Informa o CLR de uma referência de assembly que o criador de perfil planos para adicionar o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="54996-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54996-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="54996-110">Remarks</span></span>  
 <span data-ttu-id="54996-111">O CLR passa o criador de perfil uma `ICorProfilerAssemblyReferenceProvider` objeto de interface no [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="54996-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="54996-112">Isso permite que o criador de perfil informar o CLR de referências de assembly que o criador de perfil que planeja adicionar posteriormente no [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="54996-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="54996-113">.</span><span class="sxs-lookup"><span data-stu-id="54996-113">callback.</span></span> <span data-ttu-id="54996-114">Isso melhora a precisão do caminhador de fechamento de referência do assembly do CLR e de seus algoritmos para determinar se os assemblies podem ser compartilhados.</span><span class="sxs-lookup"><span data-stu-id="54996-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="54996-115">Essa interface pode ser usada somente no [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada que passa esse objeto de interface para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="54996-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54996-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54996-116">Requirements</span></span>  
 <span data-ttu-id="54996-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54996-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54996-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54996-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54996-119">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54996-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54996-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54996-120">See Also</span></span>  
 [<span data-ttu-id="54996-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="54996-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
