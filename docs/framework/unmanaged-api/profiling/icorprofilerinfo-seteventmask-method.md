---
title: "Método ICorProfilerInfo::SetEventMask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb42be7f8e5722ec9924284c257e814a186564d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="9d6c9-102">Método ICorProfilerInfo::SetEventMask</span><span class="sxs-lookup"><span data-stu-id="9d6c9-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="9d6c9-103">Determina um valor que especifica os tipos de eventos dos quais o perfil deseja receber notificação do CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9d6c9-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d6c9-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d6c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d6c9-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="9d6c9-106">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="9d6c9-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="9d6c9-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="9d6c9-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="9d6c9-108">Os bits são descritos no [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="9d6c9-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d6c9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d6c9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d6c9-110">Você deve chamar o [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método em vez desse método.</span><span class="sxs-lookup"><span data-stu-id="9d6c9-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="9d6c9-111">Embora o `SetEventMask` método continua a dar suporte, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="9d6c9-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6c9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d6c9-112">Requirements</span></span>  
 <span data-ttu-id="9d6c9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6c9-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d6c9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d6c9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d6c9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d6c9-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6c9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d6c9-117">See Also</span></span>  
 [<span data-ttu-id="9d6c9-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9d6c9-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9d6c9-119">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="9d6c9-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
