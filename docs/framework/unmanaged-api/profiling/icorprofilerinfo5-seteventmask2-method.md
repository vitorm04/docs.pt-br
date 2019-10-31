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
ms.openlocfilehash: 1e1779c0f4f36b2d7b81832bc90cf5aee0b8a7df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130390"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="af8e5-102">ICorProfilerInfo5::Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="af8e5-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="af8e5-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="af8e5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="af8e5-104">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR (Common Language runtime).</span><span class="sxs-lookup"><span data-stu-id="af8e5-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="af8e5-105">Ele fornece mais funcionalidade do que o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af8e5-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8e5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af8e5-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af8e5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af8e5-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="af8e5-108">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="af8e5-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="af8e5-109">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="af8e5-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="af8e5-110">Os bits são descritos na enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="af8e5-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="af8e5-111">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="af8e5-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="af8e5-112">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="af8e5-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="af8e5-113">Os bits são descritos na enumeração [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="af8e5-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af8e5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="af8e5-114">Remarks</span></span>  
 <span data-ttu-id="af8e5-115">O método `SetEventMask2` é usado para definir os retornos de chamada para os quais o criador de perfil se inscreve.</span><span class="sxs-lookup"><span data-stu-id="af8e5-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="af8e5-116">Normalmente, você chama o método [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) para determinar quais bits estão definidos, executar uma ou lógica de seus `pdwEventsLow` e `pdwEventsHigh` valores e novos bits que você deseja definir e, em seguida, chamar o método `SetEventMask2`.</span><span class="sxs-lookup"><span data-stu-id="af8e5-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="af8e5-117">Esse método é a alternativa recomendada para o método [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af8e5-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8e5-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af8e5-118">Requirements</span></span>  
 <span data-ttu-id="af8e5-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8e5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8e5-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="af8e5-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af8e5-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af8e5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8e5-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8e5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8e5-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af8e5-123">See also</span></span>

- [<span data-ttu-id="af8e5-124">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="af8e5-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="af8e5-125">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="af8e5-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
