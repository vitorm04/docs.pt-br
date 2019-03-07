---
title: Método ICLRSyncManager::DeleteRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0cabfe9e96ace255235f1aa7d2b80452c4d72e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482880"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="bae15-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="bae15-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="bae15-103">Solicita que o common language runtime (CLR) destruir um iterador que foi criado por uma chamada para [iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="bae15-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bae15-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bae15-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bae15-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="bae15-106">[in] O iterador que foi criado por meio de uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="bae15-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bae15-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bae15-107">Return Value</span></span>  
  
|<span data-ttu-id="bae15-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bae15-108">HRESULT</span></span>|<span data-ttu-id="bae15-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bae15-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bae15-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bae15-110">S_OK</span></span>|<span data-ttu-id="bae15-111">`DeleteRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bae15-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="bae15-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bae15-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bae15-113">O CLR não tiver sido carregado em um processo ou está em um estado em que ele não é possível executar o código gerenciado ou processar com êxito a chamada.</span><span class="sxs-lookup"><span data-stu-id="bae15-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="bae15-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bae15-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bae15-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bae15-115">The call timed out.</span></span>|  
|<span data-ttu-id="bae15-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bae15-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bae15-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="bae15-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bae15-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bae15-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bae15-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="bae15-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bae15-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bae15-120">E_FAIL</span></span>|<span data-ttu-id="bae15-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bae15-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bae15-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="bae15-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bae15-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bae15-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bae15-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="bae15-124">Remarks</span></span>  
 <span data-ttu-id="bae15-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` para garantir que sua implementação de threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="bae15-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae15-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bae15-126">Requirements</span></span>  
 <span data-ttu-id="bae15-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae15-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae15-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bae15-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bae15-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bae15-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bae15-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bae15-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae15-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae15-131">See also</span></span>
- [<span data-ttu-id="bae15-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="bae15-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="bae15-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="bae15-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
