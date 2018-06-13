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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28178cca27c257e480a7c5ec87c1925af7de4f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436410"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="3d6eb-102">Método IActionOnCLREvent::OnEvent</span><span class="sxs-lookup"><span data-stu-id="3d6eb-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="3d6eb-103">Executa os retornos de chamada em eventos registrados por meio de uma chamada para o [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d6eb-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d6eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d6eb-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="3d6eb-106">[in] Uma da [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valores, que indica o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="3d6eb-107">[in] Um ponteiro para um objeto que contém detalhes sobre `event`.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d6eb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3d6eb-108">Return Value</span></span>  
  
|<span data-ttu-id="3d6eb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d6eb-109">HRESULT</span></span>|<span data-ttu-id="3d6eb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d6eb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d6eb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d6eb-111">S_OK</span></span>|<span data-ttu-id="3d6eb-112">`OnEvent` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="3d6eb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d6eb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d6eb-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d6eb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d6eb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d6eb-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-116">The call timed out.</span></span>|  
|<span data-ttu-id="3d6eb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d6eb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d6eb-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d6eb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d6eb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d6eb-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d6eb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d6eb-121">E_FAIL</span></span>|<span data-ttu-id="3d6eb-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d6eb-123">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d6eb-124">As chamadas subsequentes para qualquer método de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d6eb-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d6eb-125">Remarks</span></span>  
 <span data-ttu-id="3d6eb-126">O `data` parâmetro é um ponteiro para um objeto do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="3d6eb-127">Se o `event` parâmetro é `Event_DomainUnload`, `data` é o identificador numérico para o <xref:System.AppDomain> que foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="3d6eb-128">O host pode levar a ação apropriada usando o identificador como uma chave.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="3d6eb-129">Se `event` é `Event_MDAFired`, `data` é um ponteiro para um [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instância que contém a mensagem de saída de um gerenciado depuração MDA (Assistente).</span><span class="sxs-lookup"><span data-stu-id="3d6eb-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="3d6eb-130">MDAs são um recurso do CLR que ajudam os desenvolvedores com depuração, ao gerar mensagens XML sobre eventos que são difíceis de interceptação.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="3d6eb-131">Essas mensagens podem ser especialmente úteis na depuração de transições entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3d6eb-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="3d6eb-132">Para obter mais informações, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="3d6eb-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d6eb-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d6eb-133">Requirements</span></span>  
 <span data-ttu-id="3d6eb-134">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d6eb-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d6eb-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d6eb-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d6eb-136">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3d6eb-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d6eb-137">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d6eb-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6eb-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d6eb-138">See Also</span></span>  
 [<span data-ttu-id="3d6eb-139">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="3d6eb-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3d6eb-140">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="3d6eb-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="3d6eb-141">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="3d6eb-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="3d6eb-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="3d6eb-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3d6eb-143">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="3d6eb-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="3d6eb-144">Estrutura MDAInfo</span><span class="sxs-lookup"><span data-stu-id="3d6eb-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
