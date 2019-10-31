---
title: Método IHostSecurityManager::SetThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: aa17f637ef71373697db5ce66e4a6540c5cc5fbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139488"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="e6236-102">Método IHostSecurityManager::SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="e6236-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="e6236-103">Define um identificador para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="e6236-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6236-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6236-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6236-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6236-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="e6236-106">no Um identificador para o token a ser definido para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="e6236-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6236-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e6236-107">Return Value</span></span>  
  
|<span data-ttu-id="e6236-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6236-108">HRESULT</span></span>|<span data-ttu-id="e6236-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6236-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6236-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6236-110">S_OK</span></span>|<span data-ttu-id="e6236-111">`SetThreadToken` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e6236-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="e6236-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6236-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6236-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e6236-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6236-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6236-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6236-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e6236-115">The call timed out.</span></span>|  
|<span data-ttu-id="e6236-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6236-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6236-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e6236-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6236-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6236-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6236-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e6236-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6236-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6236-120">E_FAIL</span></span>|<span data-ttu-id="e6236-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e6236-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6236-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e6236-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6236-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6236-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6236-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6236-124">Remarks</span></span>  
 <span data-ttu-id="e6236-125">`IHostSecurityManager::SetThreadToken` se comporta da mesma forma que a função Win32 correspondente do mesmo nome, exceto que a função Win32 permite que o chamador transmita um identificador para um thread arbitrário, enquanto `IHostSecurityManager::SetThreadToken` pode associar um token somente ao thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="e6236-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="e6236-126">O tipo de `HANDLE` não é compatível COM COM; ou seja, seu tamanho é específico para um sistema operacional e requer marshaling personalizado.</span><span class="sxs-lookup"><span data-stu-id="e6236-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="e6236-127">Portanto, esse token é para uso apenas dentro do processo, entre o CLR e o host.</span><span class="sxs-lookup"><span data-stu-id="e6236-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6236-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6236-128">Requirements</span></span>  
 <span data-ttu-id="e6236-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6236-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6236-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e6236-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6236-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e6236-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6236-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6236-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6236-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6236-133">See also</span></span>

- [<span data-ttu-id="e6236-134">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="e6236-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="e6236-135">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="e6236-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
