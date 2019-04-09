---
title: Método IHostTask::GetPriority
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 702992ab4edfea3f0b699efefedb195cd87586ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136767"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="57c51-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="57c51-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="57c51-103">Obtém o nível de prioridade do thread da tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="57c51-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57c51-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57c51-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="57c51-106">[out] Um ponteiro para um inteiro que indica o nível de prioridade do thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="57c51-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c51-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="57c51-107">Return Value</span></span>  
  
|<span data-ttu-id="57c51-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57c51-108">HRESULT</span></span>|<span data-ttu-id="57c51-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="57c51-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57c51-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57c51-110">S_OK</span></span>|`GetPriority` <span data-ttu-id="57c51-111">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="57c51-111">returned successfully.</span></span>|  
|<span data-ttu-id="57c51-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57c51-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57c51-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="57c51-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57c51-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57c51-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57c51-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="57c51-115">The call timed out.</span></span>|  
|<span data-ttu-id="57c51-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57c51-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57c51-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="57c51-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57c51-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57c51-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57c51-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="57c51-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57c51-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57c51-120">E_FAIL</span></span>|<span data-ttu-id="57c51-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="57c51-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57c51-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="57c51-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57c51-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57c51-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c51-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="57c51-124">Remarks</span></span>  
 <span data-ttu-id="57c51-125">Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função.</span><span class="sxs-lookup"><span data-stu-id="57c51-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c51-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57c51-126">Requirements</span></span>  
 <span data-ttu-id="57c51-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c51-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c51-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57c51-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57c51-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="57c51-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="57c51-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="57c51-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="57c51-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57c51-131">See also</span></span>

- [<span data-ttu-id="57c51-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="57c51-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="57c51-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="57c51-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="57c51-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="57c51-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="57c51-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="57c51-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
