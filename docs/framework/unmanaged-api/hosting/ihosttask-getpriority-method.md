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
ms.openlocfilehash: e41fcf2f03b024c1b4ae0032c0ff025d6e2aa1c3
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842498"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="38971-102">Método IHostTask::GetPriority</span><span class="sxs-lookup"><span data-stu-id="38971-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="38971-103">Obtém o nível de prioridade de thread da tarefa representada pela instância de [IHostTask](ihosttask-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="38971-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38971-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38971-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38971-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38971-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="38971-106">fora Um ponteiro para um inteiro que indica o nível de prioridade de thread da tarefa representada pela `IHostTask` instância atual.</span><span class="sxs-lookup"><span data-stu-id="38971-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38971-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="38971-107">Return Value</span></span>  
  
|<span data-ttu-id="38971-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38971-108">HRESULT</span></span>|<span data-ttu-id="38971-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="38971-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38971-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="38971-110">S_OK</span></span>|<span data-ttu-id="38971-111">`GetPriority`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38971-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="38971-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38971-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38971-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="38971-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38971-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38971-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38971-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="38971-115">The call timed out.</span></span>|  
|<span data-ttu-id="38971-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38971-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38971-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="38971-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38971-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38971-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38971-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="38971-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38971-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38971-120">E_FAIL</span></span>|<span data-ttu-id="38971-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="38971-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38971-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="38971-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38971-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38971-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38971-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="38971-124">Remarks</span></span>  
 <span data-ttu-id="38971-125">Os valores de nível de prioridade de thread são definidos pela função do Win32 `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="38971-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38971-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38971-126">Requirements</span></span>  
 <span data-ttu-id="38971-127">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38971-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38971-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38971-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38971-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38971-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38971-130">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38971-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38971-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38971-131">See also</span></span>

- [<span data-ttu-id="38971-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="38971-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="38971-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="38971-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="38971-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="38971-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="38971-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="38971-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
