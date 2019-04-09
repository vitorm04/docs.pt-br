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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4618f7ea08aa304ff5e77800cf3c0a90dd88fdbd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110911"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="baad2-102">Método IHostTaskManager::Sleep</span><span class="sxs-lookup"><span data-stu-id="baad2-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="baad2-103">Notifica o host que a tarefa atual será suspenso.</span><span class="sxs-lookup"><span data-stu-id="baad2-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baad2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baad2-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baad2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="baad2-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="baad2-106">[in] O intervalo de tempo em milissegundos, que o thread ficará suspenso.</span><span class="sxs-lookup"><span data-stu-id="baad2-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="baad2-107">[in] Um dos [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valores de enumeração que indica qual ação o host deve executar se este blocos de ação.</span><span class="sxs-lookup"><span data-stu-id="baad2-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baad2-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="baad2-108">Return Value</span></span>  
  
|<span data-ttu-id="baad2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baad2-109">HRESULT</span></span>|<span data-ttu-id="baad2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="baad2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baad2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="baad2-111">S_OK</span></span>|`Sleep` <span data-ttu-id="baad2-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="baad2-112">returned successfully.</span></span>|  
|<span data-ttu-id="baad2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="baad2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="baad2-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="baad2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="baad2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="baad2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="baad2-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="baad2-116">The call timed out.</span></span>|  
|<span data-ttu-id="baad2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="baad2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="baad2-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="baad2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="baad2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="baad2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="baad2-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="baad2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="baad2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baad2-121">E_FAIL</span></span>|<span data-ttu-id="baad2-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="baad2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="baad2-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="baad2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="baad2-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="baad2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baad2-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="baad2-125">Remarks</span></span>  
 <span data-ttu-id="baad2-126">O CLR chama normalmente `IHostTaskManager::Sleep` quando <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> é chamado do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="baad2-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baad2-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="baad2-127">Requirements</span></span>  
 <span data-ttu-id="baad2-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baad2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baad2-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="baad2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="baad2-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="baad2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="baad2-131">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="baad2-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="baad2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baad2-132">See also</span></span>

- [<span data-ttu-id="baad2-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="baad2-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="baad2-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="baad2-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="baad2-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="baad2-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="baad2-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="baad2-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
