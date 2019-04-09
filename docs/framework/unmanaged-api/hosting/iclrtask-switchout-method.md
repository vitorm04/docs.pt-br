---
title: Método ICLRTask::SwitchOut
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a215189461bd22011462842bf02ff6c0109119fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090025"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="59834-102">Método ICLRTask::SwitchOut</span><span class="sxs-lookup"><span data-stu-id="59834-102">ICLRTask::SwitchOut Method</span></span>
<span data-ttu-id="59834-103">Notifica o common language runtime (CLR) que a tarefa representada por atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância não está mais em um estado operacional.</span><span class="sxs-lookup"><span data-stu-id="59834-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59834-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59834-104">Syntax</span></span>  
  
```  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="59834-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="59834-105">Return Value</span></span>  
  
|<span data-ttu-id="59834-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59834-106">HRESULT</span></span>|<span data-ttu-id="59834-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="59834-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59834-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="59834-108">S_OK</span></span>|`SwitchOut` <span data-ttu-id="59834-109">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="59834-109">returned successfully.</span></span>|  
|<span data-ttu-id="59834-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="59834-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="59834-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="59834-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="59834-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="59834-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="59834-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="59834-113">The call timed out.</span></span>|  
|<span data-ttu-id="59834-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="59834-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="59834-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="59834-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="59834-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="59834-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="59834-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="59834-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="59834-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59834-118">E_FAIL</span></span>|<span data-ttu-id="59834-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="59834-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="59834-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="59834-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="59834-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="59834-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59834-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="59834-122">Remarks</span></span>  
 <span data-ttu-id="59834-123">Um host chama `SwitchOut` informe ao CLR que ele interrompeu a execução da tarefa que atual `ICLRTask` instância representa e reagendará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="59834-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59834-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59834-124">Requirements</span></span>  
 <span data-ttu-id="59834-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59834-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59834-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59834-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59834-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="59834-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="59834-128">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="59834-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59834-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59834-129">See also</span></span>

- [<span data-ttu-id="59834-130">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="59834-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="59834-131">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="59834-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="59834-132">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="59834-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="59834-133">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="59834-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
