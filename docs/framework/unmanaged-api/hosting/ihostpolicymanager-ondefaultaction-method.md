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
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178015"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="ca027-102">Método IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="ca027-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="ca027-103">Notifica o host de que o tempo de execução do idioma comum (CLR) está prestes a tomar a ação padrão definida <xref:System.AppDomain> por uma chamada para o método [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) em resposta a um abortamento ou descarga de thread.</span><span class="sxs-lookup"><span data-stu-id="ca027-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca027-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca027-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca027-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ca027-106">[em] Um dos valores da [Operação EClr,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) indicando o tipo de evento ao qual a CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="ca027-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="ca027-107">[em] Um dos valores do [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) indicando a ação que a CLR está tomando em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="ca027-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca027-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ca027-108">Return Value</span></span>  
  
|<span data-ttu-id="ca027-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca027-109">HRESULT</span></span>|<span data-ttu-id="ca027-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca027-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca027-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca027-111">S_OK</span></span>|<span data-ttu-id="ca027-112">`OnDefaultAction`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="ca027-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="ca027-113">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="ca027-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca027-114">A CLR não foi carregada em um processo, ou a CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="ca027-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="ca027-115">Sucesso</span><span class="sxs-lookup"><span data-stu-id="ca027-115">successfully</span></span>|  
|<span data-ttu-id="ca027-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca027-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca027-117">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="ca027-117">The call timed out.</span></span>|  
|<span data-ttu-id="ca027-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca027-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca027-119">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="ca027-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca027-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca027-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca027-121">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="ca027-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca027-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca027-122">E_FAIL</span></span>|<span data-ttu-id="ca027-123">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="ca027-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca027-124">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ca027-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca027-125">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca027-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca027-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca027-126">Requirements</span></span>  
 <span data-ttu-id="ca027-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca027-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca027-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca027-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca027-129">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca027-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca027-130">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca027-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca027-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca027-131">See also</span></span>

- [<span data-ttu-id="ca027-132">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="ca027-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="ca027-133">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="ca027-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="ca027-134">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ca027-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="ca027-135">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ca027-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
