---
title: Método IActionOnCLREvent::OnEvent
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126925"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="9d2bc-102">Método IActionOnCLREvent::OnEvent</span><span class="sxs-lookup"><span data-stu-id="9d2bc-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="9d2bc-103">Executa retornos de chamada em eventos que foram registrados usando uma chamada para o método [ICLROnEventManager:: RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d2bc-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d2bc-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d2bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d2bc-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="9d2bc-106">no Um dos valores de [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , que indica o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="9d2bc-107">no Um ponteiro para um objeto que contém detalhes sobre `event`.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d2bc-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9d2bc-108">Return Value</span></span>  
  
|<span data-ttu-id="9d2bc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d2bc-109">HRESULT</span></span>|<span data-ttu-id="9d2bc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d2bc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d2bc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d2bc-111">S_OK</span></span>|<span data-ttu-id="9d2bc-112">`OnEvent` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9d2bc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d2bc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d2bc-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d2bc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d2bc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d2bc-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-116">The call timed out.</span></span>|  
|<span data-ttu-id="9d2bc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d2bc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d2bc-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d2bc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d2bc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d2bc-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d2bc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d2bc-121">E_FAIL</span></span>|<span data-ttu-id="9d2bc-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d2bc-123">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d2bc-124">As chamadas subsequentes para qualquer método de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d2bc-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d2bc-125">Remarks</span></span>  
 <span data-ttu-id="9d2bc-126">O parâmetro `data` é um ponteiro para um objeto de tipo não especificado.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="9d2bc-127">Se o parâmetro `event` for `Event_DomainUnload`, `data` será o identificador numérico para o <xref:System.AppDomain> que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="9d2bc-128">O host pode tomar a ação apropriada usando esse identificador como uma chave.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="9d2bc-129">Se `event` for `Event_MDAFired`, `data` será um ponteiro para uma instância [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) que contém a saída da mensagem de um MDA (Assistente de depuração gerenciada).</span><span class="sxs-lookup"><span data-stu-id="9d2bc-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="9d2bc-130">MDAs são um recurso do CLR que ajuda os desenvolvedores na depuração, gerando mensagens XML sobre eventos que, de outra forma, são difíceis de interceptar.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="9d2bc-131">Essas mensagens podem ser especialmente úteis na depuração de transições entre códigos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="9d2bc-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="9d2bc-132">Para obter mais informações, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9d2bc-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2bc-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d2bc-133">Requirements</span></span>  
 <span data-ttu-id="9d2bc-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d2bc-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d2bc-135">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d2bc-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d2bc-136">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d2bc-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d2bc-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d2bc-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2bc-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d2bc-138">See also</span></span>

- [<span data-ttu-id="9d2bc-139">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="9d2bc-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9d2bc-140">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="9d2bc-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="9d2bc-141">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="9d2bc-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="9d2bc-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9d2bc-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9d2bc-143">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="9d2bc-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="9d2bc-144">Estrutura MDAInfo</span><span class="sxs-lookup"><span data-stu-id="9d2bc-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
