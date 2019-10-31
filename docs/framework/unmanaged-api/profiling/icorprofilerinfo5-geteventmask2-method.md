---
title: ICorProfilerInfo5::Método GetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114741"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="ae27d-102">ICorProfilerInfo5::Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="ae27d-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="ae27d-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="ae27d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ae27d-104">Obtém as categorias de eventos atuais para as quais o criador de perfil deseja receber notificações para o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ae27d-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="ae27d-105">Ele fornece funcionalidade não fornecida pelo método [ICorProfilerInfo:: GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ae27d-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae27d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae27d-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae27d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae27d-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="ae27d-108">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="ae27d-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="ae27d-109">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="ae27d-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ae27d-110">Os bits são descritos na enumeração [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ae27d-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="ae27d-111">[out] Um ponteiro para um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="ae27d-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="ae27d-112">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="ae27d-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ae27d-113">Os bits são descritos na enumeração [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ae27d-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae27d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae27d-114">Remarks</span></span>  
 <span data-ttu-id="ae27d-115">O método `GetEventMask2` é usado para determinar para quais retornos de chamada o criador de perfil fez assinatura.</span><span class="sxs-lookup"><span data-stu-id="ae27d-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="ae27d-116">Normalmente, você executa uma ou lógica dos valores `pdwEventsLow` e `pdwEventsHigh` e quaisquer novos bits que deseja definir e, em seguida, chama o método [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ae27d-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="ae27d-117">Esse método é a alternativa recomendada para o método [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ae27d-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae27d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae27d-118">Requirements</span></span>  
 <span data-ttu-id="ae27d-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae27d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae27d-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ae27d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae27d-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae27d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae27d-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae27d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae27d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae27d-123">See also</span></span>

- [<span data-ttu-id="ae27d-124">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="ae27d-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="ae27d-125">Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="ae27d-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
