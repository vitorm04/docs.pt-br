---
title: "Método ICorProfilerInfo::GetEventMask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8757298819f5ca6a534a12cec0593aed05610042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="f6b3b-102">Método ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="f6b3b-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="f6b3b-103">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações de eventos para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f6b3b-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6b3b-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6b3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6b3b-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="f6b3b-106">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="f6b3b-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="f6b3b-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="f6b3b-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="f6b3b-108">Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="f6b3b-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6b3b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6b3b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6b3b-110">Você deve chamar o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) método em vez desse método.</span><span class="sxs-lookup"><span data-stu-id="f6b3b-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="f6b3b-111">Embora o `SetEventMask` método continua a dar suporte, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="f6b3b-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6b3b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6b3b-112">Requirements</span></span>  
 <span data-ttu-id="f6b3b-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6b3b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6b3b-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6b3b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6b3b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6b3b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6b3b-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6b3b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b3b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6b3b-117">See Also</span></span>  
 [<span data-ttu-id="f6b3b-118">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="f6b3b-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [<span data-ttu-id="f6b3b-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f6b3b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
