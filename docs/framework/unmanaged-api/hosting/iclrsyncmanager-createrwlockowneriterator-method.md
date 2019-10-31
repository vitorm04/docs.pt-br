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
ms.openlocfilehash: fcf034d93ceb7ececd5f6c71708d442f62a00f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092261"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="c3a33-102">Método ICLRSyncManager::CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="c3a33-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="c3a33-103">Solicita que o Common Language Runtime (CLR) crie um iterador para o host usar para determinar o conjunto de tarefas que estão aguardando um bloqueio do gravador de leitor.</span><span class="sxs-lookup"><span data-stu-id="c3a33-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a33-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3a33-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a33-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3a33-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="c3a33-106">no O cookie associado ao bloqueio de leitor-gravador desejado.</span><span class="sxs-lookup"><span data-stu-id="c3a33-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="c3a33-107">fora Um ponteiro para um iterador que pode ser passado para os métodos [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) e [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3a33-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3a33-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c3a33-108">Return Value</span></span>  
  
|<span data-ttu-id="c3a33-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3a33-109">HRESULT</span></span>|<span data-ttu-id="c3a33-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3a33-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3a33-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3a33-111">S_OK</span></span>|<span data-ttu-id="c3a33-112">`CreateRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c3a33-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="c3a33-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3a33-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3a33-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c3a33-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3a33-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3a33-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3a33-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c3a33-116">The call timed out.</span></span>|  
|<span data-ttu-id="c3a33-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3a33-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3a33-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c3a33-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3a33-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3a33-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3a33-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="c3a33-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3a33-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3a33-121">E_FAIL</span></span>|<span data-ttu-id="c3a33-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c3a33-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3a33-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c3a33-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3a33-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c3a33-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c3a33-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c3a33-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c3a33-126">`CreateRWLockOwnerIterator` foi chamado em um thread que está executando código gerenciado no momento.</span><span class="sxs-lookup"><span data-stu-id="c3a33-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3a33-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3a33-127">Remarks</span></span>  
 <span data-ttu-id="c3a33-128">Normalmente, os hosts chamam os métodos `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`e `GetRWLockOwnerNext` durante a detecção de deadlocks.</span><span class="sxs-lookup"><span data-stu-id="c3a33-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="c3a33-129">O host é responsável por garantir que o bloqueio do gravador de leitor ainda seja válido, pois o CLR não faz nenhuma tentativa de manter o bloqueio do gravador de leitor ativo.</span><span class="sxs-lookup"><span data-stu-id="c3a33-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="c3a33-130">Várias estratégias estão disponíveis para o host garantir a validade do bloqueio:</span><span class="sxs-lookup"><span data-stu-id="c3a33-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="c3a33-131">O host pode bloquear chamadas de versão no bloqueio do gravador Reader (por exemplo, [IHostSemaphore:: ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) ao garantir que esse bloco não cause deadlock.</span><span class="sxs-lookup"><span data-stu-id="c3a33-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="c3a33-132">O host pode impedir que a saída Espere no objeto de evento associado ao bloqueio do gravador de leitor, garantindo novamente que esse bloco não cause o deadlock.</span><span class="sxs-lookup"><span data-stu-id="c3a33-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3a33-133">`CreateRWLockOwnerIterator` deve ser chamado somente em threads que estão executando código não gerenciado no momento.</span><span class="sxs-lookup"><span data-stu-id="c3a33-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a33-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3a33-134">Requirements</span></span>  
 <span data-ttu-id="c3a33-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a33-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a33-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3a33-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3a33-137">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3a33-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3a33-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a33-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a33-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a33-139">See also</span></span>

- [<span data-ttu-id="c3a33-140">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="c3a33-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c3a33-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="c3a33-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
