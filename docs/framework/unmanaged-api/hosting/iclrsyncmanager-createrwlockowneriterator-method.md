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
ms.openlocfilehash: 450530baed850a66327c4b1326c399529b3de67d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630584"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="a69e8-102">Método ICLRSyncManager::CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="a69e8-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="a69e8-103">Solicita que o common language runtime (CLR) cria um iterador para o host a usar para determinar o conjunto de tarefas aguardando um bloqueio de leitor-gravador.</span><span class="sxs-lookup"><span data-stu-id="a69e8-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a69e8-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a69e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a69e8-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a69e8-106">[in] O cookie associado com o bloqueio de leitor-gravador desejado.</span><span class="sxs-lookup"><span data-stu-id="a69e8-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="a69e8-107">[out] Um ponteiro para um iterador que pode ser passado para o [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) e [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="a69e8-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a69e8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a69e8-108">Return Value</span></span>  
  
|<span data-ttu-id="a69e8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a69e8-109">HRESULT</span></span>|<span data-ttu-id="a69e8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69e8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a69e8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a69e8-111">S_OK</span></span>|<span data-ttu-id="a69e8-112">`CreateRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="a69e8-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="a69e8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a69e8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a69e8-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a69e8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a69e8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a69e8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a69e8-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="a69e8-116">The call timed out.</span></span>|  
|<span data-ttu-id="a69e8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a69e8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a69e8-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a69e8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a69e8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a69e8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a69e8-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="a69e8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a69e8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a69e8-121">E_FAIL</span></span>|<span data-ttu-id="a69e8-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a69e8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a69e8-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a69e8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a69e8-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a69e8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a69e8-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a69e8-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a69e8-126">`CreateRWLockOwnerIterator` foi chamado em um thread que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a69e8-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a69e8-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a69e8-127">Remarks</span></span>  
 <span data-ttu-id="a69e8-128">Hosts normalmente chamam o `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, e `GetRWLockOwnerNext` métodos durante a detecção de deadlock.</span><span class="sxs-lookup"><span data-stu-id="a69e8-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="a69e8-129">O host é responsável por garantir que o bloqueio de leitor-gravador ainda é válido, pois o CLR não faz tentativa de manter o bloqueio de leitor-gravador ativo.</span><span class="sxs-lookup"><span data-stu-id="a69e8-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="a69e8-130">Várias estratégias estão disponíveis para o host garantir a validade do bloqueio:</span><span class="sxs-lookup"><span data-stu-id="a69e8-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="a69e8-131">O host pode bloquear chamadas de versão sobre o bloqueio de leitor-gravador (por exemplo, [ihostsemaphore:: Releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)), garantindo que este bloco não causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="a69e8-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="a69e8-132">O host pode bloquear a saída do aguardando o objeto de evento associado com o bloqueio de leitor-gravador, novamente, garantindo que este bloco não causar um deadlock.</span><span class="sxs-lookup"><span data-stu-id="a69e8-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a69e8-133">`CreateRWLockOwnerIterator` deve ser chamado apenas em threads que estão executando o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a69e8-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69e8-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a69e8-134">Requirements</span></span>  
 <span data-ttu-id="a69e8-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69e8-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69e8-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a69e8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a69e8-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a69e8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a69e8-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69e8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69e8-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a69e8-139">See also</span></span>

- [<span data-ttu-id="a69e8-140">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a69e8-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a69e8-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a69e8-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
