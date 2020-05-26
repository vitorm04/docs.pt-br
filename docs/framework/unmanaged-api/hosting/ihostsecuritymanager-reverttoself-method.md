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
ms.openlocfilehash: 456553e4cb5a6c6a557b5c3ac677fad12a5798bf
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803824"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="5526c-102">Método IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="5526c-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="5526c-103">Encerra a representação da identidade do usuário atual e retorna o token do thread original.</span><span class="sxs-lookup"><span data-stu-id="5526c-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5526c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5526c-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5526c-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5526c-105">Return Value</span></span>  
  
|<span data-ttu-id="5526c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5526c-106">HRESULT</span></span>|<span data-ttu-id="5526c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5526c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5526c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5526c-108">S_OK</span></span>|<span data-ttu-id="5526c-109">`RevertToSelf`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5526c-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="5526c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5526c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5526c-111">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5526c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5526c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5526c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5526c-113">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5526c-113">The call timed out.</span></span>|  
|<span data-ttu-id="5526c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5526c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5526c-115">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5526c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5526c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5526c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5526c-117">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="5526c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5526c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5526c-118">E_FAIL</span></span>|<span data-ttu-id="5526c-119">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5526c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5526c-120">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="5526c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5526c-121">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5526c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5526c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="5526c-122">Remarks</span></span>  
 <span data-ttu-id="5526c-123">`RevertToSelf`é chamado para retornar ao token de thread original, após uma chamada anterior para o método [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5526c-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5526c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5526c-124">Requirements</span></span>  
 <span data-ttu-id="5526c-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5526c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5526c-126">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5526c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5526c-127">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5526c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5526c-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5526c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5526c-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="5526c-129">See also</span></span>

- [<span data-ttu-id="5526c-130">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="5526c-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5526c-131">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="5526c-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="5526c-132">Método ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="5526c-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
