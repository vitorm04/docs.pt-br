---
title: Interface ICLRRuntimeHost
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247c50eb88f3b1814fd5342ded4ed3c98d4b60a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="fdd8e-102">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fdd8e-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="fdd8e-103">Fornece funcionalidade semelhante do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface fornecida no .NET Framework versão 1, com as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="fdd8e-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="fdd8e-104">A adição do [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) método para definir a interface de controle de host.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="fdd8e-105">A omissão de alguns métodos fornecidos pelo `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdd8e-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="fdd8e-106">Methods</span></span>  
  
|<span data-ttu-id="fdd8e-107">Método</span><span class="sxs-lookup"><span data-stu-id="fdd8e-107">Method</span></span>|<span data-ttu-id="fdd8e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdd8e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdd8e-109">Método ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="fdd8e-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="fdd8e-110">Usado em cenários de implantação de ClickOnce baseado no manifesto para especificar o aplicativo a ser ativado em um novo domínio.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="fdd8e-111">Método ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="fdd8e-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="fdd8e-112">Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="fdd8e-113">Método ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="fdd8e-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="fdd8e-114">Invoca o método especificado do tipo especificado no assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="fdd8e-115">Método GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="fdd8e-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="fdd8e-116">Obtém um ponteiro de interface do tipo [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que os hosts podem usar para personalizar aspectos do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fdd8e-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="fdd8e-117">Método GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="fdd8e-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="fdd8e-118">Obtém o identificador numérico do <xref:System.AppDomain> que está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="fdd8e-119">Método SetHostControl</span><span class="sxs-lookup"><span data-stu-id="fdd8e-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="fdd8e-120">Define a interface de controle de host.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-120">Sets the host control interface.</span></span> <span data-ttu-id="fdd8e-121">Você deve chamar `SetHostControl` antes de chamar `Start`.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="fdd8e-122">Método Start</span><span class="sxs-lookup"><span data-stu-id="fdd8e-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="fdd8e-123">Inicializa o CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="fdd8e-124">Método Stop</span><span class="sxs-lookup"><span data-stu-id="fdd8e-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="fdd8e-125">Interrompe a execução de código em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="fdd8e-126">Método UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="fdd8e-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="fdd8e-127">Descarrega o <xref:System.AppDomain> que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd8e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdd8e-128">Remarks</span></span>  
 <span data-ttu-id="fdd8e-129">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use o [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface para obter um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) de interface e, em seguida, chame o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método para obter um ponteiro para `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="fdd8e-130">Em versões anteriores do .NET Framework, o host obtém um ponteiro para um `ICLRRuntimeHost` instância chamando [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="fdd8e-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="fdd8e-131">Para fornecer implementações de qualquer uma das tecnologias fornecidas no .NET Framework versão 2.0, você deve usar `ICLRRuntimeHost` em vez de `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fdd8e-132">Não chame o [iniciar](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) método para ativar um aplicativo baseado no manifesto.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="fdd8e-133">Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` haverá falha na chamada de método.</span><span class="sxs-lookup"><span data-stu-id="fdd8e-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd8e-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdd8e-134">Requirements</span></span>  
 <span data-ttu-id="fdd8e-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd8e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd8e-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fdd8e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdd8e-137">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fdd8e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdd8e-138">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd8e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd8e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdd8e-139">See Also</span></span>  
 [<span data-ttu-id="fdd8e-140">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="fdd8e-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="fdd8e-141">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="fdd8e-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="fdd8e-142">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="fdd8e-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fdd8e-143">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fdd8e-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="fdd8e-144">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="fdd8e-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="fdd8e-145">Coclass CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fdd8e-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
