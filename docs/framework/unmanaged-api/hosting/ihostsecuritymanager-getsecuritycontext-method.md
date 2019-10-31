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
ms.openlocfilehash: 66aab8081a5cce8c5ba986470bc91eb0604781a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121511"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="b2743-102">Método IHostSecurityManager::GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b2743-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="b2743-103">Obtém o [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) solicitado do host.</span><span class="sxs-lookup"><span data-stu-id="b2743-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2743-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2743-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2743-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2743-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="b2743-106">no Um dos valores de [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , que indica o tipo de contexto de segurança a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="b2743-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="b2743-107">fora O endereço de um ponteiro de interface para a `IHostSecurityContext` de `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="b2743-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2743-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b2743-108">Return Value</span></span>  
  
|<span data-ttu-id="b2743-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2743-109">HRESULT</span></span>|<span data-ttu-id="b2743-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2743-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2743-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2743-111">S_OK</span></span>|<span data-ttu-id="b2743-112">`GetSecurityContext` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2743-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="b2743-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2743-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2743-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b2743-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2743-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2743-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2743-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b2743-116">The call timed out.</span></span>|  
|<span data-ttu-id="b2743-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2743-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2743-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b2743-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2743-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2743-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2743-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b2743-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2743-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2743-121">E_FAIL</span></span>|<span data-ttu-id="b2743-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b2743-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2743-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b2743-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2743-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2743-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2743-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2743-125">Remarks</span></span>  
 <span data-ttu-id="b2743-126">Um host pode controlar todo o acesso ao código para tokens de thread tanto pelo CLR quanto pelo código do usuário.</span><span class="sxs-lookup"><span data-stu-id="b2743-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="b2743-127">Ele também pode garantir que as informações completas do contexto de segurança sejam passadas entre operações assíncronas ou pontos de código com acesso restrito ao código.</span><span class="sxs-lookup"><span data-stu-id="b2743-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="b2743-128">`IHostSecurityContext` encapsula essas informações de contexto de segurança, que são opacas para o CLR.</span><span class="sxs-lookup"><span data-stu-id="b2743-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="b2743-129">O CLR captura essas informações e as move entre a expedição do item de trabalho do pool de threads, a execução do finalizador e a construção de módulo e classe.</span><span class="sxs-lookup"><span data-stu-id="b2743-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2743-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2743-130">Requirements</span></span>  
 <span data-ttu-id="b2743-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2743-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2743-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2743-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2743-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b2743-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2743-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2743-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2743-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2743-135">See also</span></span>

- [<span data-ttu-id="b2743-136">Enumeração EContextType</span><span class="sxs-lookup"><span data-stu-id="b2743-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="b2743-137">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="b2743-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="b2743-138">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="b2743-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
