---
title: "Método IHostSecurityManager::GetSecurityContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b150700c50842791a2413688583e7e1289852d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="e89f7-102">Método IHostSecurityManager::GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="e89f7-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="e89f7-103">Obtém a solicitação [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) do host.</span><span class="sxs-lookup"><span data-stu-id="e89f7-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e89f7-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e89f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e89f7-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="e89f7-106">[in] Uma da [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) valores, que indica o tipo de contexto de segurança para retornar.</span><span class="sxs-lookup"><span data-stu-id="e89f7-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="e89f7-107">[out] O endereço de um ponteiro de interface para o `IHostSecurityContext` de `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="e89f7-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e89f7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e89f7-108">Return Value</span></span>  
  
|<span data-ttu-id="e89f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e89f7-109">HRESULT</span></span>|<span data-ttu-id="e89f7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e89f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e89f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e89f7-111">S_OK</span></span>|<span data-ttu-id="e89f7-112">`GetSecurityContext`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="e89f7-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="e89f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e89f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e89f7-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e89f7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e89f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e89f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e89f7-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="e89f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="e89f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e89f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e89f7-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e89f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e89f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e89f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e89f7-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="e89f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e89f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e89f7-121">E_FAIL</span></span>|<span data-ttu-id="e89f7-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e89f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e89f7-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="e89f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e89f7-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e89f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e89f7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="e89f7-125">Remarks</span></span>  
 <span data-ttu-id="e89f7-126">Um host pode controlar o acesso de código de todos os tokens de thread pelo código do usuário e o CLR.</span><span class="sxs-lookup"><span data-stu-id="e89f7-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="e89f7-127">Ele também pode assegurar que a segurança completa informações de contexto são passadas pela operações assíncronas ou pontos de código com acesso restrito de código.</span><span class="sxs-lookup"><span data-stu-id="e89f7-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="e89f7-128">`IHostSecurityContext`encapsula essas informações de contexto de segurança, que é opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="e89f7-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="e89f7-129">O CLR captura essas informações e movê-lo em expedição de item de trabalho de pool de thread, a execução do finalizador e a construção de módulo e classe.</span><span class="sxs-lookup"><span data-stu-id="e89f7-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e89f7-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e89f7-130">Requirements</span></span>  
 <span data-ttu-id="e89f7-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e89f7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e89f7-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e89f7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e89f7-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e89f7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e89f7-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e89f7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89f7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e89f7-135">See Also</span></span>  
 [<span data-ttu-id="e89f7-136">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="e89f7-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="e89f7-137">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="e89f7-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="e89f7-138">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="e89f7-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
