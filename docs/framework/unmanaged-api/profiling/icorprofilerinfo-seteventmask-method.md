---
title: Método ICorProfilerInfo::SetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: b79668130570dc69a580fbf7da4dc122389d9ef0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136691"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="573f6-102">Método ICorProfilerInfo::SetEventMask</span><span class="sxs-lookup"><span data-stu-id="573f6-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="573f6-103">Determina um valor que especifica os tipos de eventos dos quais o perfil deseja receber notificação do CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="573f6-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="573f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="573f6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="573f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="573f6-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="573f6-106">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="573f6-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="573f6-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="573f6-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="573f6-108">Os bits são descritos na enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="573f6-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="573f6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="573f6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="573f6-110">Você deve chamar o método [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) em vez desse método.</span><span class="sxs-lookup"><span data-stu-id="573f6-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="573f6-111">Embora o método `SetEventMask` continue a ser suportado, o [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="573f6-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="573f6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="573f6-112">Requirements</span></span>  
 <span data-ttu-id="573f6-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="573f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="573f6-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="573f6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="573f6-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="573f6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="573f6-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="573f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573f6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="573f6-117">See also</span></span>

- [<span data-ttu-id="573f6-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="573f6-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="573f6-119">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="573f6-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
