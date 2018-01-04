---
title: "Método ICorRuntimeHost::CreateDomainEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2a577e1bd8765c7359e521b007bea943de7a984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="df5ed-102">Método ICorRuntimeHost::CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="df5ed-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="df5ed-103">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df5ed-103">Creates an application domain.</span></span> <span data-ttu-id="df5ed-104">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain>, para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df5ed-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="df5ed-105">Esse método permite que o chamador passar uma instância de IAppDomainSetup para configurar recursos adicionais do retornado <xref:System._AppDomain> instância.</span><span class="sxs-lookup"><span data-stu-id="df5ed-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df5ed-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df5ed-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df5ed-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df5ed-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="df5ed-108">[in] Um parâmetro opcional usado para fornecer um nome amigável para o domínio.</span><span class="sxs-lookup"><span data-stu-id="df5ed-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="df5ed-109">Esse nome amigável pode ser exibida nas interfaces do usuário, como depuradores para identificar o domínio.</span><span class="sxs-lookup"><span data-stu-id="df5ed-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="df5ed-110">[in] Um ponteiro de interface opcional do tipo `IAppDomainSetup`, obtido por uma chamada para o [Createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="df5ed-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="df5ed-111">[in] Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam a evidência mapeada por meio da política de segurança para estabelecer um conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="df5ed-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="df5ed-112">Um `IIdentity` objeto pode ser obtido chamando o [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="df5ed-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="df5ed-113">[out] Um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância de <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.</span><span class="sxs-lookup"><span data-stu-id="df5ed-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df5ed-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df5ed-114">Return Value</span></span>  
  
|<span data-ttu-id="df5ed-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df5ed-115">HRESULT</span></span>|<span data-ttu-id="df5ed-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="df5ed-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df5ed-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="df5ed-117">S_OK</span></span>|<span data-ttu-id="df5ed-118">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="df5ed-118">The operation was successful.</span></span>|  
|<span data-ttu-id="df5ed-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="df5ed-119">S_FALSE</span></span>|<span data-ttu-id="df5ed-120">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="df5ed-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="df5ed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df5ed-121">E_FAIL</span></span>|<span data-ttu-id="df5ed-122">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="df5ed-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="df5ed-123">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="df5ed-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="df5ed-124">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="df5ed-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="df5ed-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df5ed-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df5ed-126">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="df5ed-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df5ed-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="df5ed-127">Remarks</span></span>  
 <span data-ttu-id="df5ed-128">`CreateDomainEx`estende os recursos do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) , permitindo que o chamador passar um `IAppDomainSetup` instância com valores de propriedade para configurar o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df5ed-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df5ed-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df5ed-129">Requirements</span></span>  
 <span data-ttu-id="df5ed-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df5ed-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df5ed-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df5ed-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df5ed-132">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="df5ed-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df5ed-133">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="df5ed-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5ed-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df5ed-134">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="df5ed-135">Método CreateDomain</span><span class="sxs-lookup"><span data-stu-id="df5ed-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [<span data-ttu-id="df5ed-136">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="df5ed-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
