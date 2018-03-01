---
title: "Método IHostTask::Start"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db43ec56fac86b0040aa4f701940abf0d1c0df07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="747b5-102">Método IHostTask::Start</span><span class="sxs-lookup"><span data-stu-id="747b5-102">IHostTask::Start Method</span></span>
<span data-ttu-id="747b5-103">O host de move a tarefa representada por atual de solicitações [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância de um suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="747b5-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="747b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="747b5-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="747b5-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="747b5-105">Return Value</span></span>  
  
|<span data-ttu-id="747b5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="747b5-106">HRESULT</span></span>|<span data-ttu-id="747b5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="747b5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="747b5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="747b5-108">S_OK</span></span>|<span data-ttu-id="747b5-109">Inicie retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="747b5-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="747b5-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="747b5-110">E_FAIL</span></span>|<span data-ttu-id="747b5-111">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="747b5-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="747b5-112">Quando um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="747b5-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="747b5-113">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="747b5-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="747b5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="747b5-114">Remarks</span></span>  
 <span data-ttu-id="747b5-115">`Start`sempre retorna um valor HRESULT de S_OK, exceto nos casos em que ocorreu uma falha catastrófica.</span><span class="sxs-lookup"><span data-stu-id="747b5-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="747b5-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="747b5-116">Requirements</span></span>  
 <span data-ttu-id="747b5-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="747b5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="747b5-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="747b5-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="747b5-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="747b5-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="747b5-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="747b5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747b5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="747b5-121">See Also</span></span>  
 [<span data-ttu-id="747b5-122">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="747b5-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="747b5-123">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="747b5-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="747b5-124">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="747b5-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="747b5-125">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="747b5-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
