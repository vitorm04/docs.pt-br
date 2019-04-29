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
ms.openlocfilehash: 82988d25926a4e61d91a98e7cd5995dacde4e5b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763692"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="696ac-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="696ac-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="696ac-103">Solicita que o common language runtime (CLR) destruir um iterador que foi criado por uma chamada para [iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="696ac-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="696ac-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="696ac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="696ac-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="696ac-106">[in] O iterador que foi criado por meio de uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="696ac-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="696ac-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="696ac-107">Return Value</span></span>  
  
|<span data-ttu-id="696ac-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="696ac-108">HRESULT</span></span>|<span data-ttu-id="696ac-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="696ac-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="696ac-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="696ac-110">S_OK</span></span>|<span data-ttu-id="696ac-111">`DeleteRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="696ac-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="696ac-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="696ac-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="696ac-113">O CLR não tiver sido carregado em um processo ou está em um estado em que ele não é possível executar o código gerenciado ou processar com êxito a chamada.</span><span class="sxs-lookup"><span data-stu-id="696ac-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="696ac-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="696ac-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="696ac-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="696ac-115">The call timed out.</span></span>|  
|<span data-ttu-id="696ac-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="696ac-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="696ac-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="696ac-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="696ac-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="696ac-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="696ac-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="696ac-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="696ac-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="696ac-120">E_FAIL</span></span>|<span data-ttu-id="696ac-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="696ac-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="696ac-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="696ac-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="696ac-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="696ac-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="696ac-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="696ac-124">Remarks</span></span>  
 <span data-ttu-id="696ac-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` para garantir que sua implementação de threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="696ac-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696ac-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="696ac-126">Requirements</span></span>  
 <span data-ttu-id="696ac-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696ac-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696ac-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="696ac-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="696ac-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="696ac-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="696ac-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696ac-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696ac-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="696ac-131">See also</span></span>

- [<span data-ttu-id="696ac-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="696ac-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="696ac-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="696ac-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
