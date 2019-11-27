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
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449811"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="a7942-102">Método ICorProfilerInfo10:: RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="a7942-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="a7942-103">ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.</span><span class="sxs-lookup"><span data-stu-id="a7942-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7942-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7942-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a><span data-ttu-id="a7942-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7942-105">Parameters</span></span>

`dwRejitFlags` \
<span data-ttu-id="a7942-106">no Um bitmask de [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a7942-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>

`cFunctions` \
<span data-ttu-id="a7942-107">no O número de funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="a7942-107">[in] The number of functions to recompile.</span></span>

`moduleIds` \
<span data-ttu-id="a7942-108">no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="a7942-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

`methodIds` \
<span data-ttu-id="a7942-109">no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="a7942-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7942-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7942-110">Remarks</span></span>

<span data-ttu-id="a7942-111">O [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) não faz nenhum controle dos métodos embutidos.</span><span class="sxs-lookup"><span data-stu-id="a7942-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="a7942-112">O criador de perfil era esperado para bloquear a inlinhação ou controlar o Intorno e chamar `RequestReJIT` para que todos os inlineers verifiquem se cada instância de um método embutido foi ReJITted.</span><span class="sxs-lookup"><span data-stu-id="a7942-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="a7942-113">Isso representa um problema com o ReJIT na anexação, já que o criador de perfil não está presente para monitorar o inalinhamento.</span><span class="sxs-lookup"><span data-stu-id="a7942-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="a7942-114">Esse método pode ser chamado para garantir que o conjunto completo de inlineers também será ReJITted.</span><span class="sxs-lookup"><span data-stu-id="a7942-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7942-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7942-115">Requirements</span></span>

<span data-ttu-id="a7942-116">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a7942-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="a7942-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7942-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a7942-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7942-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a7942-119">**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7942-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a7942-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7942-120">See also</span></span>

- [<span data-ttu-id="a7942-121">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="a7942-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
