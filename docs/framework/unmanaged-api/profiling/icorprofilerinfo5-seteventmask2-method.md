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
ms.openlocfilehash: 10e84b729c8af607165009a8591a69dbc1afcb1e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868376"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="ed488-102">ICorProfilerInfo5::Método SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="ed488-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="ed488-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="ed488-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ed488-104">Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR (Common Language runtime).</span><span class="sxs-lookup"><span data-stu-id="ed488-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="ed488-105">Ele fornece mais funcionalidade do que o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed488-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed488-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed488-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed488-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed488-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="ed488-108">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="ed488-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="ed488-109">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="ed488-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ed488-110">Os bits são descritos na enumeração [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed488-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="ed488-111">[in] Um valor de 4 bytes que especifica as categorias de eventos.</span><span class="sxs-lookup"><span data-stu-id="ed488-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="ed488-112">Cada bit controla uma capacidade, um comportamento ou um tipo de evento diferente.</span><span class="sxs-lookup"><span data-stu-id="ed488-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ed488-113">Os bits são descritos na enumeração [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed488-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed488-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed488-114">Remarks</span></span>  
 <span data-ttu-id="ed488-115">O método `SetEventMask2` é usado para definir os retornos de chamada para os quais o criador de perfil se inscreve.</span><span class="sxs-lookup"><span data-stu-id="ed488-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="ed488-116">Normalmente, você chama o método [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) para determinar quais bits estão definidos, executar uma ou lógica de seus `pdwEventsLow` e `pdwEventsHigh` valores e novos bits que você deseja definir e, em seguida, chamar o método `SetEventMask2`.</span><span class="sxs-lookup"><span data-stu-id="ed488-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="ed488-117">Esse método é a alternativa recomendada para o método [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed488-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed488-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ed488-118">Requirements</span></span>  
 <span data-ttu-id="ed488-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed488-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed488-120">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed488-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed488-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed488-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed488-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed488-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed488-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="ed488-123">See also</span></span>

- [<span data-ttu-id="ed488-124">Interface ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="ed488-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="ed488-125">Método GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="ed488-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
