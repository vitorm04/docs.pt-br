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
ms.openlocfilehash: ffb891e61fcb34e6d33a069fc32e68865739b86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450876"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="0ebc7-102">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="0ebc7-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="0ebc7-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="0ebc7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0ebc7-104">Permite que o criador de perfil informar o common language runtime (CLR) de referências de assembly que adicionará o criador de perfil de [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ebc7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0ebc7-105">Methods</span></span>  
  
|<span data-ttu-id="0ebc7-106">Método</span><span class="sxs-lookup"><span data-stu-id="0ebc7-106">Method</span></span>|<span data-ttu-id="0ebc7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ebc7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ebc7-108">Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="0ebc7-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="0ebc7-109">Informa o CLR de uma referência de assembly que o criador de perfil planos para adicionar o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebc7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ebc7-110">Remarks</span></span>  
 <span data-ttu-id="0ebc7-111">O CLR passa o criador de perfil uma `ICorProfilerAssemblyReferenceProvider` objeto de interface no [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="0ebc7-112">Isso permite que o criador de perfil informar o CLR de referências de assembly que o criador de perfil que planeja adicionar posteriormente no [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ebc7-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="0ebc7-113">.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-113">callback.</span></span> <span data-ttu-id="0ebc7-114">Isso melhora a precisão do caminhador de fechamento de referência do assembly do CLR e de seus algoritmos para determinar se os assemblies podem ser compartilhados.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="0ebc7-115">Essa interface pode ser usada somente no [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada que passa esse objeto de interface para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="0ebc7-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebc7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ebc7-116">Requirements</span></span>  
 <span data-ttu-id="0ebc7-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebc7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebc7-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ebc7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ebc7-119">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebc7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebc7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ebc7-120">See Also</span></span>  
 [<span data-ttu-id="0ebc7-121">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="0ebc7-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
