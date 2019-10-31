---
title: Método IHostCrst::Leave
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: 050af068579d84b984ed83377d0c201e281bd154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130540"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="fee50-102">Método IHostCrst::Leave</span><span class="sxs-lookup"><span data-stu-id="fee50-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="fee50-103">Deixa a seção crítica representada pela instância atual do [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fee50-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fee50-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fee50-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fee50-105">Return Value</span></span>  
  
|<span data-ttu-id="fee50-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fee50-106">HRESULT</span></span>|<span data-ttu-id="fee50-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fee50-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fee50-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fee50-108">S_OK</span></span>|<span data-ttu-id="fee50-109">`Leave` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="fee50-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="fee50-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fee50-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fee50-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="fee50-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fee50-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fee50-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fee50-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fee50-113">The call timed out.</span></span>|  
|<span data-ttu-id="fee50-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fee50-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fee50-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="fee50-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fee50-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fee50-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fee50-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="fee50-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fee50-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fee50-118">E_FAIL</span></span>|<span data-ttu-id="fee50-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fee50-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fee50-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="fee50-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fee50-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fee50-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee50-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="fee50-122">Remarks</span></span>  
 <span data-ttu-id="fee50-123">`Leave` permite que o CLR se comunique diretamente com a implementação de Threading do host, em vez de usar a função de `LeaveCriticalSection` do Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="fee50-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="fee50-124">Um thread que assume a propriedade da seção crítica representada pela instância de `IHostCrst` atual deve chamar `Leave` uma vez para cada vez que entrar nessa seção crítica.</span><span class="sxs-lookup"><span data-stu-id="fee50-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee50-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fee50-125">Requirements</span></span>  
 <span data-ttu-id="fee50-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee50-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee50-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fee50-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fee50-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fee50-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fee50-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee50-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee50-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fee50-130">See also</span></span>

- [<span data-ttu-id="fee50-131">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="fee50-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="fee50-132">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="fee50-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="fee50-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="fee50-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
