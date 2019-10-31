---
title: Método IHostPolicyManager::OnTimeout
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: e8a14dd6a6d196cea9caa6be669b2b75a167eca8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141120"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="d7094-102">Método IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="d7094-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="d7094-103">Notifica o host que o Common Language Runtime (CLR) está prestes a executar a ação especificada por uma chamada para o método [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d7094-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7094-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7094-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7094-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7094-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="d7094-106">no Um dos valores de [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indicando o tipo de operação que atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d7094-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="d7094-107">no Um dos valores de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indicando a ação que o CLR está dando em resposta ao tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d7094-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7094-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d7094-108">Return Value</span></span>  
  
|<span data-ttu-id="d7094-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7094-109">HRESULT</span></span>|<span data-ttu-id="d7094-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7094-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7094-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7094-111">S_OK</span></span>|<span data-ttu-id="d7094-112">`OnTimeout` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d7094-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="d7094-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7094-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7094-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="d7094-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7094-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7094-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7094-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="d7094-116">The call timed out.</span></span>|  
|<span data-ttu-id="d7094-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7094-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7094-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d7094-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7094-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7094-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7094-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="d7094-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7094-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7094-121">E_FAIL</span></span>|<span data-ttu-id="d7094-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="d7094-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7094-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="d7094-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7094-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d7094-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7094-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7094-125">Requirements</span></span>  
 <span data-ttu-id="d7094-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7094-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7094-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7094-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7094-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7094-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7094-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7094-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7094-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7094-130">See also</span></span>

- [<span data-ttu-id="d7094-131">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="d7094-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="d7094-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="d7094-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d7094-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d7094-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d7094-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="d7094-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
