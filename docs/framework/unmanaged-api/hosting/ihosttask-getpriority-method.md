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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789565"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="d354b-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="d354b-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="d354b-103">Obtém o nível de prioridade do thread da tarefa representada por atual [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância.</span><span class="sxs-lookup"><span data-stu-id="d354b-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d354b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d354b-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d354b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d354b-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="d354b-106">[out] Um ponteiro para um inteiro que indica o nível de prioridade do thread da tarefa representada por atual `IHostTask` instância.</span><span class="sxs-lookup"><span data-stu-id="d354b-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d354b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d354b-107">Return Value</span></span>  
  
|<span data-ttu-id="d354b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d354b-108">HRESULT</span></span>|<span data-ttu-id="d354b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d354b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d354b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d354b-110">S_OK</span></span>|<span data-ttu-id="d354b-111">`GetPriority` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d354b-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d354b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d354b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d354b-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d354b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d354b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d354b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d354b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d354b-115">The call timed out.</span></span>|  
|<span data-ttu-id="d354b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d354b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d354b-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d354b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d354b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d354b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d354b-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="d354b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d354b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d354b-120">E_FAIL</span></span>|<span data-ttu-id="d354b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d354b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d354b-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="d354b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d354b-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d354b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d354b-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d354b-124">Remarks</span></span>  
 <span data-ttu-id="d354b-125">Valores de nível de prioridade de thread são definidos pelo Win32 `SetThreadPriority` função.</span><span class="sxs-lookup"><span data-stu-id="d354b-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d354b-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d354b-126">Requirements</span></span>  
 <span data-ttu-id="d354b-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d354b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d354b-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d354b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d354b-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d354b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d354b-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d354b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d354b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d354b-131">See also</span></span>

- [<span data-ttu-id="d354b-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="d354b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d354b-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="d354b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d354b-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="d354b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d354b-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="d354b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
