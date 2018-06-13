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
ms.openlocfilehash: eda20543c28a7b97979463928ce307df9b830103
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436014"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="a400e-102">Método ICLRSyncManager::CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="a400e-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="a400e-103">Solicita que o common language runtime (CLR) criar um iterador para o host a ser usado para determinar o conjunto de tarefas que esperam por um bloqueio de leitor / gravador.</span><span class="sxs-lookup"><span data-stu-id="a400e-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a400e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a400e-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a400e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a400e-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a400e-106">[in] O cookie associado ao bloqueio de leitor-gravador desejado.</span><span class="sxs-lookup"><span data-stu-id="a400e-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="a400e-107">[out] Um ponteiro para um iterador que pode ser passado para o [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) e [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="a400e-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a400e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a400e-108">Return Value</span></span>  
  
|<span data-ttu-id="a400e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a400e-109">HRESULT</span></span>|<span data-ttu-id="a400e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a400e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a400e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a400e-111">S_OK</span></span>|<span data-ttu-id="a400e-112">`CreateRWLockOwnerIterator` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a400e-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="a400e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a400e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a400e-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a400e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a400e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a400e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a400e-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a400e-116">The call timed out.</span></span>|  
|<span data-ttu-id="a400e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a400e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a400e-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a400e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a400e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a400e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a400e-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a400e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a400e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a400e-121">E_FAIL</span></span>|<span data-ttu-id="a400e-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a400e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a400e-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a400e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a400e-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a400e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a400e-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a400e-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a400e-126">`CreateRWLockOwnerIterator` foi chamado em um thread que está executando o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a400e-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a400e-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a400e-127">Remarks</span></span>  
 <span data-ttu-id="a400e-128">Hosts normalmente chama o `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, e `GetRWLockOwnerNext` métodos durante a detecção de deadlock.</span><span class="sxs-lookup"><span data-stu-id="a400e-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="a400e-129">O host é responsável por garantir que o bloqueio de leitor-gravador ainda é válido, porque nenhuma tentativa para manter o bloqueio de leitor-gravador ativa faz com que o CLR.</span><span class="sxs-lookup"><span data-stu-id="a400e-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="a400e-130">Várias estratégias estão disponíveis para o host garantir a validade do bloqueio:</span><span class="sxs-lookup"><span data-stu-id="a400e-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="a400e-131">O host pode bloquear chamadas de versão sobre o bloqueio de leitor-gravador (por exemplo, [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)), garantindo que esse bloco não causar deadlock.</span><span class="sxs-lookup"><span data-stu-id="a400e-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="a400e-132">O host pode bloquear a saída de esperar o objeto de evento associado com o bloqueio de leitor-gravador, novamente, garantindo que esse bloco não causar deadlock.</span><span class="sxs-lookup"><span data-stu-id="a400e-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a400e-133">`CreateRWLockOwnerIterator` deve ser chamado apenas em threads que estão executando o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a400e-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a400e-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a400e-134">Requirements</span></span>  
 <span data-ttu-id="a400e-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a400e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a400e-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a400e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a400e-137">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a400e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a400e-138">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a400e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a400e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a400e-139">See Also</span></span>  
 [<span data-ttu-id="a400e-140">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a400e-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a400e-141">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a400e-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
