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
ms.openlocfilehash: a30ac0ab8c985af04709ddd8e8e5dd9bca776dcb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759086"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="c1da5-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="c1da5-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="c1da5-103">Solicita que o common language runtime (CLR) destruir um iterador que foi criado por uma chamada para [iclrsyncmanager:: Createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="c1da5-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1da5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1da5-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1da5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1da5-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="c1da5-106">[in] O iterador que foi criado por meio de uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="c1da5-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1da5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c1da5-107">Return Value</span></span>  
  
|<span data-ttu-id="c1da5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1da5-108">HRESULT</span></span>|<span data-ttu-id="c1da5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1da5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1da5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1da5-110">S_OK</span></span>|<span data-ttu-id="c1da5-111">`DeleteRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c1da5-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="c1da5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1da5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1da5-113">O CLR não tiver sido carregado em um processo ou está em um estado em que ele não é possível executar o código gerenciado ou processar com êxito a chamada.</span><span class="sxs-lookup"><span data-stu-id="c1da5-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="c1da5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1da5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1da5-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c1da5-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1da5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1da5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1da5-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c1da5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1da5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1da5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1da5-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c1da5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1da5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1da5-120">E_FAIL</span></span>|<span data-ttu-id="c1da5-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c1da5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1da5-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c1da5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1da5-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1da5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1da5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1da5-124">Remarks</span></span>  
 <span data-ttu-id="c1da5-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` para garantir que sua implementação de threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="c1da5-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1da5-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1da5-126">Requirements</span></span>  
 <span data-ttu-id="c1da5-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1da5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1da5-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1da5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1da5-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c1da5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1da5-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1da5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1da5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1da5-131">See also</span></span>

- [<span data-ttu-id="c1da5-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c1da5-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c1da5-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c1da5-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
