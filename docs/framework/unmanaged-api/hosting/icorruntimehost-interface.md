---
title: Interface ICorRuntimeHost
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
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1280c49c2eea6a06eca10ebd8896b0722e321547
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="e7383-102">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e7383-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="e7383-103">Fornece métodos que permitem que o host iniciar e parar o common language runtime (CLR) explicitamente, para criar e configurar domínios de aplicativo, para acessar o domínio padrão e para enumerar todos os domínios em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="e7383-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="e7383-104">No .NET Framework versão 2.0, essa interface é substituída por [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e7383-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7383-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e7383-105">Methods</span></span>  
  
|<span data-ttu-id="e7383-106">Método</span><span class="sxs-lookup"><span data-stu-id="e7383-106">Method</span></span>|<span data-ttu-id="e7383-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7383-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7383-108">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="e7383-108">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|<span data-ttu-id="e7383-109">Redefine um enumerador de domínio para o início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="e7383-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="e7383-110">Método CreateDomain</span><span class="sxs-lookup"><span data-stu-id="e7383-110">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|<span data-ttu-id="e7383-111">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7383-111">Creates an application domain.</span></span> <span data-ttu-id="e7383-112">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7383-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="e7383-113">Método CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="e7383-113">CreateDomainEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|<span data-ttu-id="e7383-114">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7383-114">Creates an application domain.</span></span> <span data-ttu-id="e7383-115">Esse método permite que o chamador passar uma instância de IAppDomainSetup para configurar recursos adicionais do retornado <xref:System._AppDomain> instância.</span><span class="sxs-lookup"><span data-stu-id="e7383-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="e7383-116">Método CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="e7383-116">CreateDomainSetup Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="e7383-117">Obtém um ponteiro de interface do tipo `IAppDomainSetup` para um <xref:System.AppDomainSetup> instância.</span><span class="sxs-lookup"><span data-stu-id="e7383-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="e7383-118">`IAppDomainSetup`fornece métodos para configurar aspectos de um domínio de aplicativo antes que ele é criado.</span><span class="sxs-lookup"><span data-stu-id="e7383-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="e7383-119">Método CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="e7383-119">CreateEvidence Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|<span data-ttu-id="e7383-120">Obtém um ponteiro de interface do tipo <xref:System.Security.Principal.IIdentity>, que permite que o host criar a evidência de segurança para passar para [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).</span><span class="sxs-lookup"><span data-stu-id="e7383-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="e7383-121">Método CreateLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="e7383-121">CreateLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="e7383-122">Não use.</span><span class="sxs-lookup"><span data-stu-id="e7383-122">Do not use.</span></span>|  
|[<span data-ttu-id="e7383-123">Método CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="e7383-123">CurrentDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|<span data-ttu-id="e7383-124">Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio carregado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="e7383-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="e7383-125">Método DeleteLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="e7383-125">DeleteLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="e7383-126">Não use.</span><span class="sxs-lookup"><span data-stu-id="e7383-126">Do not use.</span></span>|  
|[<span data-ttu-id="e7383-127">Método EnumDomains</span><span class="sxs-lookup"><span data-stu-id="e7383-127">EnumDomains Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|<span data-ttu-id="e7383-128">Obtém um enumerador para os domínios no processo atual.</span><span class="sxs-lookup"><span data-stu-id="e7383-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="e7383-129">Método GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7383-129">GetConfiguration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="e7383-130">Obtém um objeto que permite que o host especificar a configuração de retorno de chamada do CLR.</span><span class="sxs-lookup"><span data-stu-id="e7383-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="e7383-131">Método GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="e7383-131">GetDefaultDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="e7383-132">Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio padrão para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="e7383-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="e7383-133">Método LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="e7383-133">LocksHeldByLogicalThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="e7383-134">Não use.</span><span class="sxs-lookup"><span data-stu-id="e7383-134">Do not use.</span></span>|  
|[<span data-ttu-id="e7383-135">Método MapFile</span><span class="sxs-lookup"><span data-stu-id="e7383-135">MapFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|<span data-ttu-id="e7383-136">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="e7383-136">Maps the specified file into memory.</span></span> <span data-ttu-id="e7383-137">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="e7383-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="e7383-138">Método NextDomain</span><span class="sxs-lookup"><span data-stu-id="e7383-138">NextDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|<span data-ttu-id="e7383-139">Obtém um ponteiro de interface para o próximo domínio na enumeração.</span><span class="sxs-lookup"><span data-stu-id="e7383-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="e7383-140">Método Start</span><span class="sxs-lookup"><span data-stu-id="e7383-140">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|<span data-ttu-id="e7383-141">Inicia o CLR.</span><span class="sxs-lookup"><span data-stu-id="e7383-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="e7383-142">Método Stop</span><span class="sxs-lookup"><span data-stu-id="e7383-142">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|<span data-ttu-id="e7383-143">Interrompe a execução de código em tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="e7383-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="e7383-144">Método SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="e7383-144">SwitchInLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="e7383-145">Não use.</span><span class="sxs-lookup"><span data-stu-id="e7383-145">Do not use.</span></span>|  
|[<span data-ttu-id="e7383-146">Método SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="e7383-146">SwitchOutLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="e7383-147">Não use.</span><span class="sxs-lookup"><span data-stu-id="e7383-147">Do not use.</span></span>|  
|[<span data-ttu-id="e7383-148">Método UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="e7383-148">UnloadDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="e7383-149">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="e7383-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7383-150">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7383-150">Requirements</span></span>  
 <span data-ttu-id="e7383-151">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7383-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7383-152">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7383-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7383-153">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e7383-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7383-154">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e7383-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7383-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7383-155">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="e7383-156">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e7383-156">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="e7383-157">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e7383-157">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="e7383-158">Hosts de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e7383-158">Runtime Hosts</span></span>](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [<span data-ttu-id="e7383-159">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e7383-159">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e7383-160">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e7383-160">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
