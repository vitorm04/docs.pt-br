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
ms.openlocfilehash: f6a4ee32d1f0bd6f66b2cd2249dd90522062cdab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120944"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="a7a01-102">Método ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="a7a01-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="a7a01-103">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações de eventos para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a7a01-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7a01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a01-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7a01-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="a7a01-106">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="a7a01-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a7a01-107">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="a7a01-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a7a01-108">Os bits são descritos na enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a7a01-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7a01-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7a01-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7a01-110">Você deve chamar o método [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) em vez desse método.</span><span class="sxs-lookup"><span data-stu-id="a7a01-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="a7a01-111">Embora o método `SetEventMask` continue a ser suportado, o [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) fornece funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="a7a01-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a01-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7a01-112">Requirements</span></span>  
 <span data-ttu-id="a7a01-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a01-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a01-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7a01-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7a01-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7a01-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7a01-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a01-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a01-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7a01-117">See also</span></span>

- [<span data-ttu-id="a7a01-118">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="a7a01-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="a7a01-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a7a01-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
