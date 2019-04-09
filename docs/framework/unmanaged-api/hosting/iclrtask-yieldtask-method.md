---
title: Método ICLRTask::YieldTask
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc8d936ac4fca704e7e3069209d8ff75d46b044d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113666"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="1c685-102">Método ICLRTask::YieldTask</span><span class="sxs-lookup"><span data-stu-id="1c685-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="1c685-103">Solicitações que o common language runtime (CLR) deixados de lado a tarefa que o atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância representa e tornar o tempo de processador disponíveis para outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="1c685-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c685-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c685-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1c685-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1c685-105">Return Value</span></span>  
  
|<span data-ttu-id="1c685-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c685-106">HRESULT</span></span>|<span data-ttu-id="1c685-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c685-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c685-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c685-108">S_OK</span></span>|`YieldTask` <span data-ttu-id="1c685-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1c685-109">returned successfully.</span></span>|  
|<span data-ttu-id="1c685-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c685-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c685-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1c685-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c685-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c685-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c685-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1c685-113">The call timed out.</span></span>|  
|<span data-ttu-id="1c685-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c685-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c685-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1c685-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c685-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c685-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c685-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="1c685-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c685-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c685-118">E_FAIL</span></span>|<span data-ttu-id="1c685-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1c685-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c685-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1c685-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c685-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c685-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c685-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c685-122">Remarks</span></span>  
 <span data-ttu-id="1c685-123">Um host chama `YieldTask` para solicitar recursos do processador para outros processos ou tarefas.</span><span class="sxs-lookup"><span data-stu-id="1c685-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="1c685-124">Este método destina-se principalmente para permitir que o código de execução longa dar tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="1c685-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="1c685-125">O tempo de execução tenta colocar a tarefa que atual `ICLRTask` instância representa em um estado em que ele pode gerar o tempo de processamento, mas não faz nenhuma garantia de êxito.</span><span class="sxs-lookup"><span data-stu-id="1c685-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c685-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c685-126">Requirements</span></span>  
 <span data-ttu-id="1c685-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c685-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c685-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1c685-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c685-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1c685-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1c685-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1c685-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c685-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c685-131">See also</span></span>

- [<span data-ttu-id="1c685-132">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="1c685-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1c685-133">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="1c685-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1c685-134">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="1c685-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1c685-135">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="1c685-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
