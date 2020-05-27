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
ms.openlocfilehash: bb12547155383bb410f592018232ca6f688bab8a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841900"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="b3774-102">Método IHostTaskManager::Sleep</span><span class="sxs-lookup"><span data-stu-id="b3774-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="b3774-103">Notifica o host que a tarefa atual vai suspender.</span><span class="sxs-lookup"><span data-stu-id="b3774-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3774-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3774-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3774-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3774-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="b3774-106">no O intervalo de tempo, em milissegundos, em que o thread será suspenso.</span><span class="sxs-lookup"><span data-stu-id="b3774-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="b3774-107">no Um dos [WAIT_OPTION](wait-option-enumeration.md) valores de enumeração, que indica a ação que o host deve executar se essa ação bloquear.</span><span class="sxs-lookup"><span data-stu-id="b3774-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3774-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b3774-108">Return Value</span></span>  
  
|<span data-ttu-id="b3774-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3774-109">HRESULT</span></span>|<span data-ttu-id="b3774-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3774-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3774-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3774-111">S_OK</span></span>|<span data-ttu-id="b3774-112">`Sleep`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3774-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="b3774-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3774-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3774-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b3774-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3774-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3774-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3774-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b3774-116">The call timed out.</span></span>|  
|<span data-ttu-id="b3774-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3774-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3774-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b3774-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3774-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3774-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3774-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b3774-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3774-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3774-121">E_FAIL</span></span>|<span data-ttu-id="b3774-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b3774-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3774-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b3774-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3774-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b3774-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3774-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3774-125">Remarks</span></span>  
 <span data-ttu-id="b3774-126">O CLR normalmente chama `IHostTaskManager::Sleep` quando <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> é chamado do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b3774-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3774-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3774-127">Requirements</span></span>  
 <span data-ttu-id="b3774-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3774-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3774-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3774-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3774-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b3774-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3774-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3774-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3774-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3774-132">See also</span></span>

- [<span data-ttu-id="b3774-133">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b3774-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b3774-134">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b3774-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b3774-135">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="b3774-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b3774-136">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b3774-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
