---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973976"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="cbdbf-102">Método ICorProfilerInfo10:: RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="cbdbf-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>
  
<span data-ttu-id="cbdbf-103">ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="cbdbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbdbf-104">Syntax</span></span>  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbdbf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbdbf-105">Parameters</span></span>  
 
 `dwRejitFlags` \
 <span data-ttu-id="cbdbf-106">no Um bitmask de [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="cbdbf-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>
 
 `cFunctions`  
 <span data-ttu-id="cbdbf-107">no O número de funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="cbdbf-108">no Especifica a `moduleId` parte dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="cbdbf-109">no Especifica a `methodId` parte dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  

## <a name="remarks"></a><span data-ttu-id="cbdbf-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbdbf-110">Remarks</span></span>  
  <span data-ttu-id="cbdbf-111">O [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) não faz nenhum controle dos métodos embutidos.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="cbdbf-112">O criador de perfil era esperado para bloquear a linhagem ou controlar a inlinhação e chamar `RequestReJIT` todos os inlineers para garantir que cada instância de um método embutido fosse ReJITted.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="cbdbf-113">Isso representa um problema com o ReJIT na anexação, já que o criador de perfil não está presente para monitorar o inalinhamento.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="cbdbf-114">Esse método pode ser chamado para garantir que o conjunto completo de inlineers também será ReJITted.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>  

## <a name="requirements"></a><span data-ttu-id="cbdbf-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbdbf-115">Requirements</span></span>  
 <span data-ttu-id="cbdbf-116">**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="cbdbf-116">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="cbdbf-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbdbf-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbdbf-118">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbdbf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbdbf-119">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbdbf-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cbdbf-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbdbf-120">See also</span></span>
- [<span data-ttu-id="cbdbf-121">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="cbdbf-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

