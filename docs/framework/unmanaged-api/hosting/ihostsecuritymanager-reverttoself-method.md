---
title: "Método IHostSecurityManager::RevertToSelf"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.RevertToSelf
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0fad325bc3df54f412a797e9944f5b1f38615786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="76a4d-102">Método IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="76a4d-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="76a4d-103">Finaliza a representação da identidade do usuário atual e retorna o token de thread original.</span><span class="sxs-lookup"><span data-stu-id="76a4d-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a4d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76a4d-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="76a4d-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="76a4d-105">Return Value</span></span>  
  
|<span data-ttu-id="76a4d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76a4d-106">HRESULT</span></span>|<span data-ttu-id="76a4d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="76a4d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76a4d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="76a4d-108">S_OK</span></span>|<span data-ttu-id="76a4d-109">`RevertToSelf`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="76a4d-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="76a4d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76a4d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76a4d-111">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="76a4d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76a4d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76a4d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76a4d-113">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="76a4d-113">The call timed out.</span></span>|  
|<span data-ttu-id="76a4d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76a4d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76a4d-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="76a4d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76a4d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76a4d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76a4d-117">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="76a4d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76a4d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76a4d-118">E_FAIL</span></span>|<span data-ttu-id="76a4d-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="76a4d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76a4d-120">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="76a4d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76a4d-121">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76a4d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76a4d-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="76a4d-122">Remarks</span></span>  
 <span data-ttu-id="76a4d-123">`RevertToSelf`é chamado para retornar para o token de thread original, após uma chamada anterior para o [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="76a4d-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a4d-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76a4d-124">Requirements</span></span>  
 <span data-ttu-id="76a4d-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76a4d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a4d-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76a4d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76a4d-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="76a4d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76a4d-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76a4d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a4d-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76a4d-129">See Also</span></span>  
 [<span data-ttu-id="76a4d-130">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="76a4d-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="76a4d-131">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="76a4d-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="76a4d-132">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="76a4d-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
