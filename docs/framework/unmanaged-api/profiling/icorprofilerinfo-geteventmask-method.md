---
title: Método ICorProfilerInfo::GetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4852df791b179f1a5ee130bd185be8527c14b7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541918"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="7f1e7-102">Método ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="7f1e7-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="7f1e7-103">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações de eventos para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7f1e7-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f1e7-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f1e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f1e7-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="7f1e7-106">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="7f1e7-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="7f1e7-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="7f1e7-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="7f1e7-108">Os bits são descritos na [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="7f1e7-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f1e7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f1e7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f1e7-110">Você deve chamar o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) em vez deste método.</span><span class="sxs-lookup"><span data-stu-id="7f1e7-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="7f1e7-111">Embora o `SetEventMask` método continua a ter suporte, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="7f1e7-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1e7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f1e7-112">Requirements</span></span>  
 <span data-ttu-id="7f1e7-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1e7-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f1e7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f1e7-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f1e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f1e7-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1e7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f1e7-117">See also</span></span>
- [<span data-ttu-id="7f1e7-118">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="7f1e7-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="7f1e7-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7f1e7-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
