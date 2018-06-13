---
title: ICorProfilerInfo5::Método SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc1cfadd809b7406845596ace78e308ccbf529a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455991"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="24ef3-102">ICorProfilerInfo5::Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="24ef3-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="24ef3-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="24ef3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="24ef3-104">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do tempo de execução de linguagem comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="24ef3-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="24ef3-105">Ele fornece a funcionalidade mais do que o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="24ef3-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ef3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24ef3-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24ef3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24ef3-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="24ef3-108">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="24ef3-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="24ef3-109">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="24ef3-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="24ef3-110">Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="24ef3-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="24ef3-111">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="24ef3-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="24ef3-112">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="24ef3-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="24ef3-113">Os bits são descritos no [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="24ef3-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24ef3-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="24ef3-114">Remarks</span></span>  
 <span data-ttu-id="24ef3-115">O método `SetEventMask2` é usado para definir os retornos de chamada para os quais o criador de perfil se inscreve.</span><span class="sxs-lookup"><span data-stu-id="24ef3-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="24ef3-116">Normalmente, você chama o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) método para determinar quais bits são definidos, execute um ou lógico de seu `pdwEventsLow` e `pdwEventsHigh` valores e quaisquer novos bits que você deseja definir e, em seguida, chamar o `SetEventMask2` método.</span><span class="sxs-lookup"><span data-stu-id="24ef3-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="24ef3-117">Esse método é a alternativa recomendada para o [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="24ef3-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ef3-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24ef3-118">Requirements</span></span>  
 <span data-ttu-id="24ef3-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24ef3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24ef3-120">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24ef3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24ef3-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24ef3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24ef3-122">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24ef3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ef3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24ef3-123">See Also</span></span>  
 [<span data-ttu-id="24ef3-124">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="24ef3-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="24ef3-125">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="24ef3-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
