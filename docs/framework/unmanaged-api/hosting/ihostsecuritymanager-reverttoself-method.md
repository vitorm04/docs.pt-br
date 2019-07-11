---
title: Método IHostSecurityManager::RevertToSelf
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f098d8462229a405d5775203368478c7ee7e9f3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769392"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="8374b-102">Método IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="8374b-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="8374b-103">Finaliza a representação da identidade do usuário atual e retorna o token do thread original.</span><span class="sxs-lookup"><span data-stu-id="8374b-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8374b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8374b-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8374b-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8374b-105">Return Value</span></span>  
  
|<span data-ttu-id="8374b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8374b-106">HRESULT</span></span>|<span data-ttu-id="8374b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8374b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8374b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8374b-108">S_OK</span></span>|<span data-ttu-id="8374b-109">`RevertToSelf` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8374b-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="8374b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8374b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8374b-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8374b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8374b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8374b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8374b-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8374b-113">The call timed out.</span></span>|  
|<span data-ttu-id="8374b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8374b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8374b-115">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8374b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8374b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8374b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8374b-117">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8374b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8374b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8374b-118">E_FAIL</span></span>|<span data-ttu-id="8374b-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8374b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8374b-120">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8374b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8374b-121">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8374b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8374b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8374b-122">Remarks</span></span>  
 <span data-ttu-id="8374b-123">`RevertToSelf` é chamado para retornar para o token do thread original, após uma chamada anterior para o [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8374b-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8374b-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8374b-124">Requirements</span></span>  
 <span data-ttu-id="8374b-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8374b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8374b-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8374b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8374b-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8374b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8374b-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8374b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8374b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8374b-129">See also</span></span>

- [<span data-ttu-id="8374b-130">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="8374b-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="8374b-131">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="8374b-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="8374b-132">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="8374b-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
