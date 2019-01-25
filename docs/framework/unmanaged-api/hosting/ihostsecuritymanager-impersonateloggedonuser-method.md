---
title: Método IHostSecurityManager::ImpersonateLoggedOnUser
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ceb199e027b111c8e29166d3b91027a3df2d534e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658605"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="46657-102">Método IHostSecurityManager::ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="46657-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="46657-103">As solicitações que o código ser executado usando as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="46657-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46657-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46657-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46657-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="46657-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="46657-106">[in] Um token que representa as credenciais do usuário a ser representado.</span><span class="sxs-lookup"><span data-stu-id="46657-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46657-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="46657-107">Return Value</span></span>  
  
|<span data-ttu-id="46657-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46657-108">HRESULT</span></span>|<span data-ttu-id="46657-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="46657-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46657-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="46657-110">S_OK</span></span>|<span data-ttu-id="46657-111">`ImpersonateLoggedOnUser` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="46657-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="46657-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46657-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46657-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="46657-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="46657-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46657-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46657-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="46657-115">The call timed out.</span></span>|  
|<span data-ttu-id="46657-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46657-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46657-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="46657-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46657-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46657-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46657-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="46657-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46657-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46657-120">E_FAIL</span></span>|<span data-ttu-id="46657-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="46657-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46657-122">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="46657-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46657-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="46657-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46657-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="46657-124">Remarks</span></span>  
 <span data-ttu-id="46657-125">Chamar `LogonUser` ou uma função relacionada do Win32 para obter um identificador para as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="46657-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="46657-126">O `HANDLE` tipo não é compatível com, ou seja, seu tamanho é específico para um sistema operacional e ela requer o marshaling personalizado.</span><span class="sxs-lookup"><span data-stu-id="46657-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="46657-127">Portanto, esse token é para uso somente dentro do processo, entre o CLR e o host.</span><span class="sxs-lookup"><span data-stu-id="46657-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46657-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46657-128">Requirements</span></span>  
 <span data-ttu-id="46657-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46657-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46657-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46657-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46657-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="46657-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46657-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46657-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46657-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46657-133">See also</span></span>
- [<span data-ttu-id="46657-134">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="46657-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="46657-135">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="46657-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="46657-136">Método RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="46657-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
