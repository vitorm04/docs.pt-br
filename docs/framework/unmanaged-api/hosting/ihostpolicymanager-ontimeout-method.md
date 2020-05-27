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
ms.openlocfilehash: fb0f943d710322257d052edc5c16108671622790
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804216"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="2f94b-102">Método IHostPolicyManager::OnTimeout</span><span class="sxs-lookup"><span data-stu-id="2f94b-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="2f94b-103">Notifica o host que o Common Language Runtime (CLR) está prestes a executar a ação especificada por uma chamada para o método [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2f94b-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f94b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f94b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f94b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f94b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="2f94b-106">no Um dos valores de [EClrOperation](eclroperation-enumeration.md) , indicando o tipo de operação que atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2f94b-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="2f94b-107">no Um dos valores de [EPolicyAction](epolicyaction-enumeration.md) , indicando a ação que o CLR está dando em resposta ao tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2f94b-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f94b-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2f94b-108">Return Value</span></span>  
  
|<span data-ttu-id="2f94b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f94b-109">HRESULT</span></span>|<span data-ttu-id="2f94b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f94b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f94b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f94b-111">S_OK</span></span>|<span data-ttu-id="2f94b-112">`OnTimeout`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2f94b-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="2f94b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f94b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f94b-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2f94b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f94b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f94b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f94b-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2f94b-116">The call timed out.</span></span>|  
|<span data-ttu-id="2f94b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f94b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f94b-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2f94b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f94b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f94b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f94b-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="2f94b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f94b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f94b-121">E_FAIL</span></span>|<span data-ttu-id="2f94b-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2f94b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f94b-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2f94b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f94b-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f94b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f94b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f94b-125">Requirements</span></span>  
 <span data-ttu-id="2f94b-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f94b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f94b-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f94b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f94b-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f94b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f94b-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f94b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f94b-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f94b-130">See also</span></span>

- [<span data-ttu-id="2f94b-131">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="2f94b-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="2f94b-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="2f94b-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="2f94b-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2f94b-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="2f94b-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2f94b-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
