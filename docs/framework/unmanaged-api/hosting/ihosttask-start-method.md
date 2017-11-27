---
title: "Método IHostTask::Start"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1a289099245228b8806639cb98f579bc56317b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="4b9b6-102">Método IHostTask::Start</span><span class="sxs-lookup"><span data-stu-id="4b9b6-102">IHostTask::Start Method</span></span>
<span data-ttu-id="4b9b6-103">O host de move a tarefa representada por atual de solicitações [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância de um suspenso para um estado ativo, no qual o código pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b9b6-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b9b6-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4b9b6-105">Return Value</span></span>  
  
|<span data-ttu-id="4b9b6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b9b6-106">HRESULT</span></span>|<span data-ttu-id="4b9b6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b9b6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b9b6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b9b6-108">S_OK</span></span>|<span data-ttu-id="4b9b6-109">Inicie retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="4b9b6-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b9b6-110">E_FAIL</span></span>|<span data-ttu-id="4b9b6-111">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b9b6-112">Quando um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="4b9b6-113">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b9b6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b9b6-114">Remarks</span></span>  
 <span data-ttu-id="4b9b6-115">`Start`sempre retorna um valor HRESULT de S_OK, exceto nos casos em que ocorreu uma falha catastrófica.</span><span class="sxs-lookup"><span data-stu-id="4b9b6-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b9b6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b9b6-116">Requirements</span></span>  
 <span data-ttu-id="4b9b6-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b9b6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b9b6-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b9b6-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b9b6-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4b9b6-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b9b6-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b9b6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9b6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b9b6-121">See Also</span></span>  
 [<span data-ttu-id="4b9b6-122">Interface ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4b9b6-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4b9b6-123">Interface ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4b9b6-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4b9b6-124">Interface IHostTask</span><span class="sxs-lookup"><span data-stu-id="4b9b6-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4b9b6-125">Interface IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4b9b6-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
