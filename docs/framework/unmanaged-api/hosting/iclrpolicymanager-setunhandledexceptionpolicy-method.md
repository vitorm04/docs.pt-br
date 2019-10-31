---
title: Método ICLRPolicyManager::SetUnhandledExceptionPolicy
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 7b6a4be94e526e7b464b336d221eff936808635a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120568"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="7e8e8-102">Método ICLRPolicyManager::SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="7e8e8-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="7e8e8-103">Especifica o comportamento do Common Language Runtime (CLR) quando ocorre uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e8e8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e8e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e8e8-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="7e8e8-106">no Um dos valores de [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) , indicando se o comportamento é definido pelo CLR ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e8e8-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7e8e8-107">Return Value</span></span>  
  
|<span data-ttu-id="7e8e8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e8e8-108">HRESULT</span></span>|<span data-ttu-id="7e8e8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e8e8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e8e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e8e8-110">S_OK</span></span>|<span data-ttu-id="7e8e8-111">`SetUnhandledExceptionPolicy` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="7e8e8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e8e8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e8e8-113">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e8e8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e8e8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e8e8-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-115">The call timed out.</span></span>|  
|<span data-ttu-id="7e8e8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e8e8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e8e8-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e8e8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e8e8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e8e8-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e8e8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e8e8-120">E_FAIL</span></span>|<span data-ttu-id="7e8e8-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e8e8-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e8e8-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e8e8-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="7e8e8-124">Remarks</span></span>  
 <span data-ttu-id="7e8e8-125">Por padrão, o CLR é o manipulador final para todas as exceções sem tratamento e seu comportamento padrão é subdividir o processo.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="7e8e8-126">O host pode alterar esse comportamento definindo o valor de `policy` como eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="7e8e8-127">Esse valor permite que o host implemente seu próprio comportamento padrão, como nas versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="7e8e8-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e8e8-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e8e8-128">Requirements</span></span>  
 <span data-ttu-id="7e8e8-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e8e8-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e8e8-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7e8e8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e8e8-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e8e8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e8e8-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e8e8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8e8-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e8e8-133">See also</span></span>

- [<span data-ttu-id="7e8e8-134">Enumeração EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="7e8e8-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="7e8e8-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7e8e8-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7e8e8-136">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7e8e8-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="7e8e8-137">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7e8e8-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
