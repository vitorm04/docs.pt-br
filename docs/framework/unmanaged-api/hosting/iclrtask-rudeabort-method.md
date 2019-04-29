---
title: Método ICLRTask::RudeAbort
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db47f90e73922858013885e99e953ddcacbd450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763510"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="f67f7-102">Método ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="f67f7-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="f67f7-103">Instrui o common language runtime (CLR) para anular a tarefa representada por atual [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância imediatamente e incondicionalmente.</span><span class="sxs-lookup"><span data-stu-id="f67f7-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f67f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f67f7-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="f67f7-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f67f7-105">Return Value</span></span>  
  
|<span data-ttu-id="f67f7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f67f7-106">HRESULT</span></span>|<span data-ttu-id="f67f7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f67f7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f67f7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f67f7-108">S_OK</span></span>|<span data-ttu-id="f67f7-109">`RudeAbort` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f67f7-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="f67f7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f67f7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f67f7-111">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f67f7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f67f7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f67f7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f67f7-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f67f7-113">The call timed out.</span></span>|  
|<span data-ttu-id="f67f7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f67f7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f67f7-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f67f7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f67f7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f67f7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f67f7-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="f67f7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f67f7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f67f7-118">E_FAIL</span></span>|<span data-ttu-id="f67f7-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f67f7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f67f7-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f67f7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f67f7-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f67f7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f67f7-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="f67f7-122">Remarks</span></span>  
 <span data-ttu-id="f67f7-123">Um host chama `RudeAbort` para anular uma tarefa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f67f7-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="f67f7-124">Os finalizadores e rotinas de tratamento de exceção não são garantidos para ser executado.</span><span class="sxs-lookup"><span data-stu-id="f67f7-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f67f7-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f67f7-125">Requirements</span></span>  
 <span data-ttu-id="f67f7-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f67f7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f67f7-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f67f7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f67f7-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f67f7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f67f7-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f67f7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67f7-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f67f7-130">See also</span></span>

- [<span data-ttu-id="f67f7-131">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f67f7-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f67f7-132">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f67f7-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f67f7-133">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="f67f7-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f67f7-134">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f67f7-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
