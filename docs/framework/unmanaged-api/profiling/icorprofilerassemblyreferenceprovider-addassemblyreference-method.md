---
title: ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference
ms.date: 03/30/2017
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
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866722"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="a7e29-102">ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="a7e29-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="a7e29-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a7e29-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a7e29-104">Informa o Common Language Runtime (CLR) de uma referência de assembly que o criador de perfil planeja adicionar ao retorno de chamada [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a7e29-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e29-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7e29-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e29-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7e29-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="a7e29-107">Um ponteiro para uma estrutura de [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) que fornece ao CLR informações sobre uma referência de assembly que deve ser considerada ao executar uma movimentação de fechamento de referência de assembly.</span><span class="sxs-lookup"><span data-stu-id="a7e29-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a7e29-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7e29-108">Remarks</span></span>  
 <span data-ttu-id="a7e29-109">O criador de perfil chama esse método para cada assembly de destino que planeja fazer referência a partir do assembly especificado no argumento `wszAssemblyPath` do retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a7e29-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="a7e29-110">O objeto da interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) é passado para o retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) do criador de perfil, juntamente com o caminho e o nome do assembly no argumento `wszAssemblyPath`.</span><span class="sxs-lookup"><span data-stu-id="a7e29-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e29-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a7e29-111">Requirements</span></span>  
 <span data-ttu-id="a7e29-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7e29-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e29-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7e29-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7e29-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7e29-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7e29-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e29-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e29-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="a7e29-116">See also</span></span>

- [<span data-ttu-id="a7e29-117">Interface ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="a7e29-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="a7e29-118">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="a7e29-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="a7e29-119">Método ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="a7e29-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
