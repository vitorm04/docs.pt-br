---
title: "Método ICLRSyncManager::DeleteRWLockOwnerIterator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.DeleteRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3df37a9572c47ce4b4a5080f6aed3f307adba360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="223b9-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="223b9-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="223b9-103">Solicita que o common language runtime (CLR) destruir um iterador que foi criado por uma chamada para [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="223b9-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="223b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="223b9-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="223b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="223b9-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="223b9-106">[in] O iterador que foi criado usando uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="223b9-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="223b9-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="223b9-107">Return Value</span></span>  
  
|<span data-ttu-id="223b9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="223b9-108">HRESULT</span></span>|<span data-ttu-id="223b9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="223b9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="223b9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="223b9-110">S_OK</span></span>|<span data-ttu-id="223b9-111">`DeleteRWLockOwnerIterator`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="223b9-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="223b9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="223b9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="223b9-113">O CLR não foi carregado em um processo ou está em um estado em que ele não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="223b9-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="223b9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="223b9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="223b9-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="223b9-115">The call timed out.</span></span>|  
|<span data-ttu-id="223b9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="223b9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="223b9-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="223b9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="223b9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="223b9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="223b9-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="223b9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="223b9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="223b9-120">E_FAIL</span></span>|<span data-ttu-id="223b9-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="223b9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="223b9-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="223b9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="223b9-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="223b9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="223b9-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="223b9-124">Remarks</span></span>  
 <span data-ttu-id="223b9-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` para garantir que sua implementação de threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="223b9-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="223b9-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="223b9-126">Requirements</span></span>  
 <span data-ttu-id="223b9-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="223b9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="223b9-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="223b9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="223b9-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="223b9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="223b9-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="223b9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223b9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="223b9-131">See Also</span></span>  
 [<span data-ttu-id="223b9-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="223b9-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="223b9-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="223b9-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
