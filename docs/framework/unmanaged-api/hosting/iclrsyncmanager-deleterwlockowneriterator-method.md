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
ms.openlocfilehash: fb02b5c941e15d172140565e8efb625234947cd7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130572"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="f2910-102">Método ICLRSyncManager::DeleteRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="f2910-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="f2910-103">Solicita que o Common Language Runtime (CLR) destrua um iterador criado por uma chamada para [ICLRSyncManager:: CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2910-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2910-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2910-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2910-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2910-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="f2910-106">no O iterador criado usando uma chamada para `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="f2910-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2910-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f2910-107">Return Value</span></span>  
  
|<span data-ttu-id="f2910-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2910-108">HRESULT</span></span>|<span data-ttu-id="f2910-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2910-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2910-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2910-110">S_OK</span></span>|<span data-ttu-id="f2910-111">`DeleteRWLockOwnerIterator` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2910-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="f2910-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2910-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2910-113">O CLR não foi carregado em um processo ou está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f2910-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="f2910-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2910-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2910-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="f2910-115">The call timed out.</span></span>|  
|<span data-ttu-id="f2910-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2910-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2910-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f2910-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2910-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2910-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2910-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="f2910-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2910-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2910-120">E_FAIL</span></span>|<span data-ttu-id="f2910-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f2910-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2910-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="f2910-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2910-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f2910-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2910-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2910-124">Remarks</span></span>  
 <span data-ttu-id="f2910-125">O host pode chamar esse método e `CreateRWLockOwnerIterator` para garantir que sua implementação de Threading permaneça sincronizada.</span><span class="sxs-lookup"><span data-stu-id="f2910-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2910-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2910-126">Requirements</span></span>  
 <span data-ttu-id="f2910-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2910-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2910-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2910-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2910-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f2910-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2910-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2910-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2910-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2910-131">See also</span></span>

- [<span data-ttu-id="f2910-132">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="f2910-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f2910-133">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="f2910-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
