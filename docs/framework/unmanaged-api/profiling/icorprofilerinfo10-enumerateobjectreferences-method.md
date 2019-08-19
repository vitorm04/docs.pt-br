---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974026"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="2aede-102">Método ICorProfilerInfo10:: EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="2aede-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>
  
 <span data-ttu-id="2aede-103">Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).</span><span class="sxs-lookup"><span data-stu-id="2aede-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="2aede-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2aede-104">Syntax</span></span>  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aede-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2aede-105">Parameters</span></span>  

 `objectId` \
 <span data-ttu-id="2aede-106">no O objeto no qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="2aede-106">[in] The object to enumerate references on.</span></span>

 `callback` \
 <span data-ttu-id="2aede-107">no A função que será chamada com as referências para o objeto.</span><span class="sxs-lookup"><span data-stu-id="2aede-107">[in] The function that will be called with the references for the object.</span></span>

 `clientData` \
 <span data-ttu-id="2aede-108">no Dados fornecidos pelo criador de perfil para passar `callback` para a função.</span><span class="sxs-lookup"><span data-stu-id="2aede-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2aede-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2aede-109">Remarks</span></span>  
 <span data-ttu-id="2aede-110">O método `EnumerateObjectReferences` é semelhante a [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), exceto pelo fato de que ele percorre as referências sob demanda para o criador de perfil em vez de alocar previamente uma matriz para armazenar as referências.</span><span class="sxs-lookup"><span data-stu-id="2aede-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>  

## <a name="requirements"></a><span data-ttu-id="2aede-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2aede-111">Requirements</span></span>  
 <span data-ttu-id="2aede-112">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="2aede-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="2aede-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2aede-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2aede-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aede-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aede-115">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aede-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2aede-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aede-116">See also</span></span>
- [<span data-ttu-id="2aede-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="2aede-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

