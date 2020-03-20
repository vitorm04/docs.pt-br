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
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178014"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="0c79d-102">Método IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="0c79d-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="0c79d-103">Notifica o host de que o tempo de execução do idioma comum (CLR) está prestes a tomar a ação especificada por uma chamada para o [método ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo hámenos.</span><span class="sxs-lookup"><span data-stu-id="0c79d-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c79d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c79d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c79d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c79d-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="0c79d-106">[em] Um dos valores da [Operação EClr,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) indicando o tipo de operação que se esvaiu.</span><span class="sxs-lookup"><span data-stu-id="0c79d-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="0c79d-107">[em] Um dos valores do [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) indicando a ação que a CLR está tomando em resposta ao tempo há10.</span><span class="sxs-lookup"><span data-stu-id="0c79d-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c79d-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0c79d-108">Return Value</span></span>  
  
|<span data-ttu-id="0c79d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c79d-109">HRESULT</span></span>|<span data-ttu-id="0c79d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c79d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c79d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c79d-111">S_OK</span></span>|<span data-ttu-id="0c79d-112">`OnTimeout`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0c79d-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="0c79d-113">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="0c79d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c79d-114">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0c79d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c79d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c79d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c79d-116">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="0c79d-116">The call timed out.</span></span>|  
|<span data-ttu-id="0c79d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c79d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c79d-118">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="0c79d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c79d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c79d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c79d-120">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="0c79d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c79d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c79d-121">E_FAIL</span></span>|<span data-ttu-id="0c79d-122">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="0c79d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c79d-123">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="0c79d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c79d-124">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c79d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c79d-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c79d-125">Requirements</span></span>  
 <span data-ttu-id="0c79d-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c79d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c79d-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c79d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c79d-128">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c79d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c79d-129">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c79d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c79d-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c79d-130">See also</span></span>

- [<span data-ttu-id="0c79d-131">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="0c79d-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="0c79d-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="0c79d-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="0c79d-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0c79d-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="0c79d-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0c79d-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
