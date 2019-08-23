---
title: Método ICLRSyncManager::CreateRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64179e132cfaffbb1fcdc2cd0a47bbcc11be2ff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943266"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="507bd-102">Método ICLRSyncManager::CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="507bd-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="507bd-103">Solicita que o Common Language Runtime (CLR) crie um iterador para o host usar para determinar o conjunto de tarefas que estão aguardando um bloqueio do gravador de leitor.</span><span class="sxs-lookup"><span data-stu-id="507bd-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="507bd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="507bd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="507bd-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="507bd-106">no O cookie associado ao bloqueio de leitor-gravador desejado.</span><span class="sxs-lookup"><span data-stu-id="507bd-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="507bd-107">fora Um ponteiro para um iterador que pode ser passado para os métodos [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) e [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="507bd-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="507bd-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="507bd-108">Return Value</span></span>  
  
|<span data-ttu-id="507bd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="507bd-109">HRESULT</span></span>|<span data-ttu-id="507bd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="507bd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="507bd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="507bd-111">S_OK</span></span>|<span data-ttu-id="507bd-112">`CreateRWLockOwnerIterator`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="507bd-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="507bd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="507bd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="507bd-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="507bd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="507bd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="507bd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="507bd-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="507bd-116">The call timed out.</span></span>|  
|<span data-ttu-id="507bd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="507bd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="507bd-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="507bd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="507bd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="507bd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="507bd-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="507bd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="507bd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="507bd-121">E_FAIL</span></span>|<span data-ttu-id="507bd-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="507bd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="507bd-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="507bd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="507bd-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="507bd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="507bd-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="507bd-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="507bd-126">`CreateRWLockOwnerIterator`foi chamado em um thread que está executando código gerenciado no momento.</span><span class="sxs-lookup"><span data-stu-id="507bd-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="507bd-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="507bd-127">Remarks</span></span>  
 <span data-ttu-id="507bd-128">Normalmente, os hosts `DeleteRWLockOwnerIterator`chamam os `GetRWLockOwnerNext` `CreateRWLockOwnerIterator`métodos, e durante a detecção de deadlock.</span><span class="sxs-lookup"><span data-stu-id="507bd-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="507bd-129">O host é responsável por garantir que o bloqueio do gravador de leitor ainda seja válido, pois o CLR não faz nenhuma tentativa de manter o bloqueio do gravador de leitor ativo.</span><span class="sxs-lookup"><span data-stu-id="507bd-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="507bd-130">Várias estratégias estão disponíveis para o host garantir a validade do bloqueio:</span><span class="sxs-lookup"><span data-stu-id="507bd-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="507bd-131">O host pode bloquear chamadas de versão no bloqueio do gravador Reader (por exemplo, [IHostSemaphore:: ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) ao garantir que esse bloco não cause deadlock.</span><span class="sxs-lookup"><span data-stu-id="507bd-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="507bd-132">O host pode impedir que a saída Espere no objeto de evento associado ao bloqueio do gravador de leitor, garantindo novamente que esse bloco não cause o deadlock.</span><span class="sxs-lookup"><span data-stu-id="507bd-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="507bd-133">`CreateRWLockOwnerIterator`deve ser chamado somente em threads que estão executando código não gerenciado no momento.</span><span class="sxs-lookup"><span data-stu-id="507bd-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507bd-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="507bd-134">Requirements</span></span>  
 <span data-ttu-id="507bd-135">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="507bd-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507bd-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="507bd-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="507bd-137">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="507bd-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="507bd-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507bd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507bd-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="507bd-139">See also</span></span>

- [<span data-ttu-id="507bd-140">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="507bd-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="507bd-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="507bd-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
