---
title: "Enumeração COR_PRF_HIGH_MONITOR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df931796b32b6bea49e8b69da02d39e6a4803e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="23ad8-102">Enumeração COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="23ad8-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="23ad8-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="23ad8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="23ad8-104">Fornece sinalizadores além daqueles encontrados no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração que o criador de perfil pode especificar para o [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método quando ele está sendo carregado.</span><span class="sxs-lookup"><span data-stu-id="23ad8-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ad8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23ad8-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="23ad8-106">Membros</span><span class="sxs-lookup"><span data-stu-id="23ad8-106">Members</span></span>  
  
|<span data-ttu-id="23ad8-107">Membro</span><span class="sxs-lookup"><span data-stu-id="23ad8-107">Member</span></span>|<span data-ttu-id="23ad8-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="23ad8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="23ad8-109">Nenhum sinalizador está definido.</span><span class="sxs-lookup"><span data-stu-id="23ad8-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="23ad8-110">Controles de [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada para a adição de referências de assembly durante a movimentação de fechamento de referência de assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="23ad8-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="23ad8-111">Controles de [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) retorno de chamada para as atualizações para o fluxo de símbolo associado a um módulo de memória.</span><span class="sxs-lookup"><span data-stu-id="23ad8-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="23ad8-112">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que necessitam de imagens aprimoradas por perfil.</span><span class="sxs-lookup"><span data-stu-id="23ad8-112">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="23ad8-113">Ele corresponde do `COR_PRF_REQUIRE_PROFILE_IMAGE` sinalizador no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="23ad8-113">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="23ad8-114">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="23ad8-114">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="23ad8-115">Representa todos os sinalizadores `COR_PRF_HIGH_MONITOR` que podem ser definidos apenas durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="23ad8-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="23ad8-116">Tentar alterar qualquer um desses sinalizadores em outro lugar resulta em um valor de `HRESULT` que indica falha.</span><span class="sxs-lookup"><span data-stu-id="23ad8-116">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ad8-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="23ad8-117">Remarks</span></span>  
 <span data-ttu-id="23ad8-118">O `COR_PRF_HIGH_MONITOR` sinalizadores são usados com o `pdwEventsHigh` parâmetro o [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) e [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="23ad8-118">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
 <span data-ttu-id="23ad8-119">Começando com o [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], o valor da `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` alterada de 0 a `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="23ad8-119">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ad8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23ad8-120">Requirements</span></span>  
 <span data-ttu-id="23ad8-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ad8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ad8-122">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23ad8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23ad8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23ad8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23ad8-124">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ad8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ad8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23ad8-125">See Also</span></span>  
 [<span data-ttu-id="23ad8-126">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="23ad8-126">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="23ad8-127">Enumeração COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="23ad8-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="23ad8-128">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="23ad8-128">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
