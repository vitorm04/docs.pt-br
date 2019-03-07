---
title: Método IHostSecurityManager::GetSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d17609e585f6e0ecd685d893bb0f8b3e4c0fe0cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484818"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="57151-102">Método IHostSecurityManager::GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="57151-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="57151-103">Obtém o solicitada [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.</span><span class="sxs-lookup"><span data-stu-id="57151-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57151-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57151-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57151-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57151-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="57151-106">[in] Um dos [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valores, que indica o tipo do contexto de segurança para retornar.</span><span class="sxs-lookup"><span data-stu-id="57151-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="57151-107">[out] O endereço de um ponteiro de interface para o `IHostSecurityContext` de `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="57151-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57151-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="57151-108">Return Value</span></span>  
  
|<span data-ttu-id="57151-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57151-109">HRESULT</span></span>|<span data-ttu-id="57151-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="57151-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57151-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57151-111">S_OK</span></span>|<span data-ttu-id="57151-112">`GetSecurityContext` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="57151-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="57151-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57151-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57151-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="57151-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57151-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57151-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57151-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="57151-116">The call timed out.</span></span>|  
|<span data-ttu-id="57151-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57151-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57151-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="57151-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57151-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57151-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57151-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="57151-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57151-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57151-121">E_FAIL</span></span>|<span data-ttu-id="57151-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="57151-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57151-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="57151-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57151-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57151-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57151-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="57151-125">Remarks</span></span>  
 <span data-ttu-id="57151-126">Um host pode controlar todo o acesso de código para tokens de thread pelo código do usuário e o CLR.</span><span class="sxs-lookup"><span data-stu-id="57151-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="57151-127">Ele também pode garantir que a segurança completa informações de contexto são passadas entre os pontos de código com acesso de código restrito ou operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="57151-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="57151-128">`IHostSecurityContext` encapsula a essas informações de contexto de segurança, que é opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="57151-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="57151-129">O CLR captura essas informações e a move entre despacho de item de trabalho de pool de threads, execução do finalizador e construção de módulo e classe.</span><span class="sxs-lookup"><span data-stu-id="57151-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57151-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57151-130">Requirements</span></span>  
 <span data-ttu-id="57151-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57151-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57151-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57151-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57151-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="57151-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57151-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57151-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57151-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57151-135">See also</span></span>
- [<span data-ttu-id="57151-136">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="57151-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="57151-137">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="57151-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="57151-138">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="57151-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
