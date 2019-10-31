---
title: Método IHostTaskManager::Sleep
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: 7eedf052b6f2285799940b394d9891975230cb72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132922"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="f5757-102">Método IHostTaskManager::Sleep</span><span class="sxs-lookup"><span data-stu-id="f5757-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="f5757-103">Notifica o host que a tarefa atual vai suspender.</span><span class="sxs-lookup"><span data-stu-id="f5757-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5757-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5757-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5757-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5757-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="f5757-106">no O intervalo de tempo, em milissegundos, em que o thread será suspenso.</span><span class="sxs-lookup"><span data-stu-id="f5757-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="f5757-107">no Um dos valores de enumeração [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , que indica a ação que o host deve tomar se essa ação bloquear.</span><span class="sxs-lookup"><span data-stu-id="f5757-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5757-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f5757-108">Return Value</span></span>  
  
|<span data-ttu-id="f5757-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5757-109">HRESULT</span></span>|<span data-ttu-id="f5757-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5757-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5757-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5757-111">S_OK</span></span>|<span data-ttu-id="f5757-112">`Sleep` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f5757-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="f5757-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5757-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5757-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f5757-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5757-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5757-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5757-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f5757-116">The call timed out.</span></span>|  
|<span data-ttu-id="f5757-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5757-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5757-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f5757-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5757-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5757-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5757-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f5757-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5757-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5757-121">E_FAIL</span></span>|<span data-ttu-id="f5757-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f5757-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5757-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f5757-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5757-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5757-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5757-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5757-125">Remarks</span></span>  
 <span data-ttu-id="f5757-126">O CLR normalmente chama `IHostTaskManager::Sleep` quando <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> é chamado do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="f5757-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5757-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5757-127">Requirements</span></span>  
 <span data-ttu-id="f5757-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5757-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5757-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5757-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5757-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5757-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5757-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5757-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5757-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5757-132">See also</span></span>

- [<span data-ttu-id="f5757-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f5757-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f5757-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f5757-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f5757-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f5757-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f5757-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f5757-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
