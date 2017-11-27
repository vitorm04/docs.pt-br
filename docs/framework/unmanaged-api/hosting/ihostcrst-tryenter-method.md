---
title: "Método IHostCrst::TryEnter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.TryEnter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6b622666c3bda806c77329d0d0a10726b4838c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="d2a50-102">Método IHostCrst::TryEnter</span><span class="sxs-lookup"><span data-stu-id="d2a50-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="d2a50-103">Tentativas de entrar na seção crítica representada pelo atual [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="d2a50-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2a50-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2a50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2a50-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="d2a50-106">[in] Uma da [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores, que indica qual ação o host deve executar se os blocos de operação.</span><span class="sxs-lookup"><span data-stu-id="d2a50-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="d2a50-107">[out] `true` se a seção crítica pode ser inserida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d2a50-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2a50-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d2a50-108">Return Value</span></span>  
  
|<span data-ttu-id="d2a50-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2a50-109">HRESULT</span></span>|<span data-ttu-id="d2a50-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2a50-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2a50-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2a50-111">S_OK</span></span>|<span data-ttu-id="d2a50-112">`TryEnter`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="d2a50-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="d2a50-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2a50-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2a50-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d2a50-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2a50-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2a50-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2a50-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="d2a50-116">The call timed out.</span></span>|  
|<span data-ttu-id="d2a50-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2a50-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2a50-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d2a50-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2a50-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2a50-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2a50-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="d2a50-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2a50-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2a50-121">E_FAIL</span></span>|<span data-ttu-id="d2a50-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d2a50-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2a50-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d2a50-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2a50-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2a50-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a50-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2a50-125">Remarks</span></span>  
 <span data-ttu-id="d2a50-126">`TryEnter`retorna imediatamente e indica se o thread de chamada inserido na seção crítica.</span><span class="sxs-lookup"><span data-stu-id="d2a50-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="d2a50-127">Esse método reflete o Wind32 `TryEnterCriticalSection` função.</span><span class="sxs-lookup"><span data-stu-id="d2a50-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a50-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2a50-128">Requirements</span></span>  
 <span data-ttu-id="d2a50-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2a50-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a50-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2a50-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2a50-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d2a50-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2a50-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a50-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a50-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2a50-133">See Also</span></span>  
 [<span data-ttu-id="d2a50-134">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="d2a50-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d2a50-135">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="d2a50-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="d2a50-136">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="d2a50-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
