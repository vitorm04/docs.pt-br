---
title: Método IHostPolicyManager::OnDefaultAction
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: cdf0a720ac440d156b5b8bdc8dc2c78d3bb5ba86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128555"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="38811-102">Método IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="38811-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="38811-103">Notifica o host que o Common Language Runtime (CLR) está prestes a executar a ação padrão que foi definida por uma chamada para o método [ICLRPolicyManager:: Setpadrãoaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) em resposta a uma anulação de thread ou <xref:System.AppDomain> descarregamento.</span><span class="sxs-lookup"><span data-stu-id="38811-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38811-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38811-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38811-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38811-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="38811-106">no Um dos valores de [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indicando o tipo de evento para o qual o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="38811-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="38811-107">no Um dos valores de [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indicando a ação que o CLR está realizando em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="38811-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38811-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="38811-108">Return Value</span></span>  
  
|<span data-ttu-id="38811-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38811-109">HRESULT</span></span>|<span data-ttu-id="38811-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="38811-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38811-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="38811-111">S_OK</span></span>|<span data-ttu-id="38811-112">`OnDefaultAction` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="38811-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="38811-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38811-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38811-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="38811-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="38811-115">com êxito</span><span class="sxs-lookup"><span data-stu-id="38811-115">successfully</span></span>|  
|<span data-ttu-id="38811-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38811-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38811-117">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="38811-117">The call timed out.</span></span>|  
|<span data-ttu-id="38811-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38811-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38811-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="38811-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38811-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38811-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38811-121">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="38811-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38811-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38811-122">E_FAIL</span></span>|<span data-ttu-id="38811-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="38811-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38811-124">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="38811-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38811-125">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38811-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38811-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38811-126">Requirements</span></span>  
 <span data-ttu-id="38811-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38811-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38811-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38811-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38811-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38811-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38811-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38811-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38811-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38811-131">See also</span></span>

- [<span data-ttu-id="38811-132">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="38811-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="38811-133">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="38811-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="38811-134">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="38811-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="38811-135">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="38811-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
