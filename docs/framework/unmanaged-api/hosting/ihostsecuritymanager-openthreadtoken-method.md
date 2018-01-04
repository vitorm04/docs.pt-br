---
title: "Método IHostSecurityManager::OpenThreadToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.OpenThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="aa1d9-102">Método IHostSecurityManager::OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="aa1d9-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="aa1d9-103">Abre o token de acesso discricionário associado ao thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa1d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa1d9-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa1d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa1d9-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="aa1d9-106">[in] Uma máscara de valores de acesso que especificam os tipos solicitados de acesso para o token de thread.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="aa1d9-107">Esses valores são definidos em Win32 `OpenThreadToken` função.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="aa1d9-108">Os tipos de acesso solicitado reconciliadas em relação a lista de controle de acesso discricionário (DACL) para determinar quais tipos de acesso para conceder ou negar do token.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="aa1d9-109">[in] `true` para especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o thread de chamada; `false` para especificar que a verificação de acesso deve ser executada usando o contexto de segurança para o thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="aa1d9-110">Se o thread está representando um cliente, o contexto de segurança pode ser de um processo do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="aa1d9-111">[out] Um ponteiro para o token de acesso aberto recentemente.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa1d9-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="aa1d9-112">Return Value</span></span>  
  
|<span data-ttu-id="aa1d9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa1d9-113">HRESULT</span></span>|<span data-ttu-id="aa1d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa1d9-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa1d9-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa1d9-115">S_OK</span></span>|<span data-ttu-id="aa1d9-116">`OpenThreadToken`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="aa1d9-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa1d9-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa1d9-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa1d9-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa1d9-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa1d9-120">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-120">The call timed out.</span></span>|  
|<span data-ttu-id="aa1d9-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa1d9-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa1d9-122">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa1d9-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa1d9-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa1d9-124">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa1d9-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa1d9-125">E_FAIL</span></span>|<span data-ttu-id="aa1d9-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa1d9-127">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa1d9-128">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa1d9-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa1d9-129">Remarks</span></span>  
 <span data-ttu-id="aa1d9-130">`IHostSecurityManager::OpenThreadToken`se comporta da mesma forma para a função Win32 correspondente de mesmo nome, exceto que a função Win32 permite que o chamador passar um identificador para um thread arbitrário, enquanto `IHostSecurityManager::OpenThreadToken` abre apenas o token associado com o thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="aa1d9-131">O `HANDLE` tipo não é compatível com o COM, ou seja, seu tamanho é específico para o sistema operacional e requer empacotamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="aa1d9-132">Portanto, esse token é para uso somente dentro do processo, entre o host e o CLR.</span><span class="sxs-lookup"><span data-stu-id="aa1d9-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa1d9-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa1d9-133">Requirements</span></span>  
 <span data-ttu-id="aa1d9-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa1d9-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa1d9-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa1d9-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa1d9-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="aa1d9-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa1d9-137">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa1d9-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1d9-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa1d9-138">See Also</span></span>  
 [<span data-ttu-id="aa1d9-139">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="aa1d9-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="aa1d9-140">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="aa1d9-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
