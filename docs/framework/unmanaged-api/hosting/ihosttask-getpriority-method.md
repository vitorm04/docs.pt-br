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
ms.openlocfilehash: b722963290ec9713d4dc991cc4135473da96b42e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764526"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="7bed5-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="7bed5-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="7bed5-103">Obtém o nível de prioridade do thread da tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="7bed5-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bed5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bed5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bed5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bed5-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="7bed5-106">[out] Um ponteiro para um inteiro que indica o nível de prioridade do thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="7bed5-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bed5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7bed5-107">Return Value</span></span>  
  
|<span data-ttu-id="7bed5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bed5-108">HRESULT</span></span>|<span data-ttu-id="7bed5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bed5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bed5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bed5-110">S_OK</span></span>|<span data-ttu-id="7bed5-111">`GetPriority` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7bed5-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="7bed5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bed5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bed5-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7bed5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bed5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bed5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bed5-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7bed5-115">The call timed out.</span></span>|  
|<span data-ttu-id="7bed5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bed5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bed5-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7bed5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bed5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bed5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bed5-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="7bed5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bed5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bed5-120">E_FAIL</span></span>|<span data-ttu-id="7bed5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7bed5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bed5-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7bed5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bed5-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7bed5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bed5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bed5-124">Remarks</span></span>  
 <span data-ttu-id="7bed5-125">Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função.</span><span class="sxs-lookup"><span data-stu-id="7bed5-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bed5-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bed5-126">Requirements</span></span>  
 <span data-ttu-id="7bed5-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bed5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bed5-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7bed5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bed5-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7bed5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bed5-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bed5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bed5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bed5-131">See also</span></span>

- [<span data-ttu-id="7bed5-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7bed5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7bed5-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7bed5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="7bed5-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="7bed5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7bed5-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7bed5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
