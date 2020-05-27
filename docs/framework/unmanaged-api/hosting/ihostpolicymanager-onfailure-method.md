---
title: Método IHostPolicyManager::OnFailure
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 8ad4943aa9bf1b66b34bcd83a5422a977b16518d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804226"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="c52fd-102">Método IHostPolicyManager::OnFailure</span><span class="sxs-lookup"><span data-stu-id="c52fd-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="c52fd-103">Notifica o host de que o Common Language Runtime (CLR) está prestes a executar a ação especificada por uma chamada para o método [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) em resposta a uma falha de alocação ou de recuperação de recurso.</span><span class="sxs-lookup"><span data-stu-id="c52fd-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c52fd-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c52fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c52fd-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="c52fd-106">no Um dos valores de [EClrFailure](eclrfailure-enumeration.md) , indicando o tipo de falha em que o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="c52fd-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="c52fd-107">no Um dos valores de [EPolicyAction](epolicyaction-enumeration.md) , indicando a ação que o CLR está fazendo em resposta a `failure` .</span><span class="sxs-lookup"><span data-stu-id="c52fd-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c52fd-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="c52fd-108">Return Value</span></span>  
  
|<span data-ttu-id="c52fd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c52fd-109">HRESULT</span></span>|<span data-ttu-id="c52fd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c52fd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c52fd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c52fd-111">S_OK</span></span>|<span data-ttu-id="c52fd-112">`OnFailure`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c52fd-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="c52fd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c52fd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c52fd-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c52fd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c52fd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c52fd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c52fd-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c52fd-116">The call timed out.</span></span>|  
|<span data-ttu-id="c52fd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c52fd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c52fd-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c52fd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c52fd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c52fd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c52fd-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="c52fd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c52fd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c52fd-121">E_FAIL</span></span>|<span data-ttu-id="c52fd-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c52fd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c52fd-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c52fd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c52fd-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c52fd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c52fd-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c52fd-125">Requirements</span></span>  
 <span data-ttu-id="c52fd-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c52fd-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c52fd-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c52fd-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c52fd-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c52fd-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c52fd-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c52fd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52fd-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="c52fd-130">See also</span></span>

- [<span data-ttu-id="c52fd-131">Enumeração EClrFailure</span><span class="sxs-lookup"><span data-stu-id="c52fd-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="c52fd-132">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="c52fd-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c52fd-133">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c52fd-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c52fd-134">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c52fd-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
