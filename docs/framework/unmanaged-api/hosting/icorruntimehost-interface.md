---
title: Interface ICorRuntimeHost
ms.date: 03/30/2017
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
ms.openlocfilehash: 420f22a242a20f8bdf5d5b84f47a297a2f503db0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546015"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="f48d2-102">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f48d2-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="f48d2-103">Fornece métodos que permitem ao host iniciar e parar explicitamente o Common Language Runtime (CLR), criar e configurar domínios de aplicativo, acessar o domínio padrão e enumerar todos os domínios em execução no processo.</span><span class="sxs-lookup"><span data-stu-id="f48d2-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="f48d2-104">Na versão .NET Framework 2,0, essa interface é substituída por [ICLRRuntimeHost](iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f48d2-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f48d2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f48d2-105">Methods</span></span>  
  
|<span data-ttu-id="f48d2-106">Método</span><span class="sxs-lookup"><span data-stu-id="f48d2-106">Method</span></span>|<span data-ttu-id="f48d2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f48d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f48d2-108">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="f48d2-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="f48d2-109">Redefine um enumerador de domínio de volta para o início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="f48d2-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="f48d2-110">Método CreateDomain</span><span class="sxs-lookup"><span data-stu-id="f48d2-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="f48d2-111">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f48d2-111">Creates an application domain.</span></span> <span data-ttu-id="f48d2-112">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f48d2-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="f48d2-113">Método CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="f48d2-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="f48d2-114">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f48d2-114">Creates an application domain.</span></span> <span data-ttu-id="f48d2-115">Esse método permite que o chamador passe uma instância de IAppDomainSetup para configurar recursos adicionais da <xref:System._AppDomain> instância retornada.</span><span class="sxs-lookup"><span data-stu-id="f48d2-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="f48d2-116">Método CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="f48d2-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="f48d2-117">Obtém um ponteiro de interface do tipo `IAppDomainSetup` para uma <xref:System.AppDomainSetup> instância.</span><span class="sxs-lookup"><span data-stu-id="f48d2-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="f48d2-118">`IAppDomainSetup` fornece métodos para configurar aspectos de um domínio de aplicativo antes de sua criação.</span><span class="sxs-lookup"><span data-stu-id="f48d2-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="f48d2-119">Método CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="f48d2-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="f48d2-120">Obtém um ponteiro de interface do tipo <xref:System.Security.Principal.IIdentity> , que permite que o host crie evidências de segurança para passar para [CreateDomain](icorruntimehost-createdomain-method.md) ou [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span><span class="sxs-lookup"><span data-stu-id="f48d2-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="f48d2-121">Método CreateLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="f48d2-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="f48d2-122">Não use.</span><span class="sxs-lookup"><span data-stu-id="f48d2-122">Do not use.</span></span>|  
|[<span data-ttu-id="f48d2-123">Método CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="f48d2-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="f48d2-124">Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio carregado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="f48d2-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="f48d2-125">Método DeleteLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="f48d2-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="f48d2-126">Não use.</span><span class="sxs-lookup"><span data-stu-id="f48d2-126">Do not use.</span></span>|  
|[<span data-ttu-id="f48d2-127">Método EnumDomains</span><span class="sxs-lookup"><span data-stu-id="f48d2-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="f48d2-128">Obtém um enumerador para os domínios no processo atual.</span><span class="sxs-lookup"><span data-stu-id="f48d2-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="f48d2-129">Método GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="f48d2-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="f48d2-130">Obtém um objeto que permite ao host especificar a configuração de retorno de chamada do CLR.</span><span class="sxs-lookup"><span data-stu-id="f48d2-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="f48d2-131">Método GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="f48d2-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="f48d2-132">Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio padrão para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="f48d2-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="f48d2-133">Método LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="f48d2-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="f48d2-134">Não use.</span><span class="sxs-lookup"><span data-stu-id="f48d2-134">Do not use.</span></span>|  
|[<span data-ttu-id="f48d2-135">Método MapFile</span><span class="sxs-lookup"><span data-stu-id="f48d2-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="f48d2-136">Mapeia o arquivo especificado na memória.</span><span class="sxs-lookup"><span data-stu-id="f48d2-136">Maps the specified file into memory.</span></span> <span data-ttu-id="f48d2-137">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f48d2-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="f48d2-138">Método NextDomain</span><span class="sxs-lookup"><span data-stu-id="f48d2-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="f48d2-139">Obtém um ponteiro de interface para o próximo domínio na enumeração.</span><span class="sxs-lookup"><span data-stu-id="f48d2-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="f48d2-140">Método de início</span><span class="sxs-lookup"><span data-stu-id="f48d2-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="f48d2-141">Inicia o CLR.</span><span class="sxs-lookup"><span data-stu-id="f48d2-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="f48d2-142">Método Stop</span><span class="sxs-lookup"><span data-stu-id="f48d2-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="f48d2-143">Interrompe a execução do código no tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="f48d2-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="f48d2-144">Método SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="f48d2-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="f48d2-145">Não use.</span><span class="sxs-lookup"><span data-stu-id="f48d2-145">Do not use.</span></span>|  
|[<span data-ttu-id="f48d2-146">Método SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="f48d2-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="f48d2-147">Não use.</span><span class="sxs-lookup"><span data-stu-id="f48d2-147">Do not use.</span></span>|  
|[<span data-ttu-id="f48d2-148">Método UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="f48d2-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="f48d2-149">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="f48d2-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f48d2-150">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f48d2-150">Requirements</span></span>  
 <span data-ttu-id="f48d2-151">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f48d2-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f48d2-152">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f48d2-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f48d2-153">**Biblioteca:** Incluído como um recurso no MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f48d2-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f48d2-154">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="f48d2-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48d2-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="f48d2-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="f48d2-156">Hosting</span><span class="sxs-lookup"><span data-stu-id="f48d2-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="f48d2-157">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f48d2-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="f48d2-158">[Hosts de runtime](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f48d2-158">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="f48d2-159">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="f48d2-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f48d2-160">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f48d2-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
