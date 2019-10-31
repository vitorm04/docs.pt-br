---
title: Método IHostSecurityContext::Capture
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121530"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="d4054-102">Método IHostSecurityContext::Capture</span><span class="sxs-lookup"><span data-stu-id="d4054-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="d4054-103">Obtém um clone da instância [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) retornada de uma chamada para [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="d4054-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4054-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4054-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4054-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4054-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="d4054-106">fora Um ponteiro para o endereço de um clone do objeto de `IHostSecurityContext` a ser capturado.</span><span class="sxs-lookup"><span data-stu-id="d4054-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4054-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d4054-107">Return Value</span></span>  
  
|<span data-ttu-id="d4054-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4054-108">HRESULT</span></span>|<span data-ttu-id="d4054-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4054-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4054-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4054-110">S_OK</span></span>|<span data-ttu-id="d4054-111">`Capture` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d4054-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="d4054-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4054-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4054-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d4054-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4054-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4054-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4054-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d4054-115">The call timed out.</span></span>|  
|<span data-ttu-id="d4054-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4054-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4054-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d4054-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4054-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4054-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4054-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d4054-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4054-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4054-120">E_FAIL</span></span>|<span data-ttu-id="d4054-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d4054-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4054-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d4054-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4054-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4054-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4054-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4054-124">Remarks</span></span>  
 <span data-ttu-id="d4054-125">O ponteiro de interface retornado de `Capture` é um clone do contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="d4054-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="d4054-126">Quando essas informações são movidas em um ponto de código assíncrono, seu tempo de vida é separado do ponteiro no qual a chamada foi feita.</span><span class="sxs-lookup"><span data-stu-id="d4054-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="d4054-127">Portanto, o ponteiro original pode ser liberado.</span><span class="sxs-lookup"><span data-stu-id="d4054-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4054-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4054-128">Requirements</span></span>  
 <span data-ttu-id="d4054-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4054-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4054-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4054-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4054-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4054-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4054-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4054-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4054-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4054-133">See also</span></span>

- [<span data-ttu-id="d4054-134">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="d4054-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d4054-135">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="d4054-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
