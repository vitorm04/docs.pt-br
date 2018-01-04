---
title: "ICorProfilerInfo5::Método GetEventMask2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerInfo5.GetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72adbbdc3495f4171f555d119cb61d5dbc5ef0e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="5753b-102">ICorProfilerInfo5::Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="5753b-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="5753b-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="5753b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5753b-104">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5753b-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="5753b-105">Ele fornece funcionalidade não fornecida pelo [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5753b-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5753b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5753b-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5753b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5753b-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="5753b-108">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="5753b-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="5753b-109">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="5753b-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="5753b-110">Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="5753b-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="5753b-111">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="5753b-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="5753b-112">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="5753b-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="5753b-113">Os bits são descritos no [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="5753b-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5753b-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5753b-114">Remarks</span></span>  
 <span data-ttu-id="5753b-115">O método `GetEventMask2` é usado para determinar para quais retornos de chamada o criador de perfil fez assinatura.</span><span class="sxs-lookup"><span data-stu-id="5753b-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="5753b-116">Geralmente, você executa um OR lógico do `pdwEventsLow` e `pdwEventsHigh` valores e quaisquer novos bits que você deseja definir e, em seguida, chamar o [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5753b-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="5753b-117">Esse método é a alternativa recomendada para o [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="5753b-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5753b-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5753b-118">Requirements</span></span>  
 <span data-ttu-id="5753b-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5753b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5753b-120">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5753b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5753b-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5753b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5753b-122">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5753b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5753b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5753b-123">See Also</span></span>  
 [<span data-ttu-id="5753b-124">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="5753b-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="5753b-125">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="5753b-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
