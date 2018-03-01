---
title: "ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 292d814c1a3f66b415e9a7b6220d8ee921f6b949
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="32ed4-102">ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="32ed4-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="32ed4-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="32ed4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="32ed4-104">Informa o common language runtime (CLR) de uma referência de assembly que o criador de perfil planos para adicionar o [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="32ed4-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ed4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32ed4-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32ed4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32ed4-106">Parameters</span></span>  
 <span data-ttu-id="32ed4-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="32ed4-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="32ed4-108">Um ponteiro para um [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) estrutura que fornece informações sobre uma referência de assembly devem ser consideradas ao executar um exame de fechamento de referência de assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="32ed4-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ed4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="32ed4-109">Remarks</span></span>  
 <span data-ttu-id="32ed4-110">O criador de perfil chama esse método para cada assembly de destino, ela planeja fazer referência do assembly especificado no `wszAssemblyPath` argumento o [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="32ed4-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="32ed4-111">O [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) o objeto de interface é passado para o criador de perfil [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada, juntamente com o caminho do assembly e o nome do `wszAssemblyPath` argumento.</span><span class="sxs-lookup"><span data-stu-id="32ed4-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ed4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32ed4-112">Requirements</span></span>  
 <span data-ttu-id="32ed4-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ed4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ed4-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32ed4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32ed4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32ed4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ed4-116">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ed4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ed4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32ed4-117">See Also</span></span>  
 [<span data-ttu-id="32ed4-118">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="32ed4-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [<span data-ttu-id="32ed4-119">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="32ed4-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="32ed4-120">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="32ed4-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
