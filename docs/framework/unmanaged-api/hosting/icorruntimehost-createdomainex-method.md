---
title: Método ICorRuntimeHost::CreateDomainEx
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a538f14e7dbf24a94343f364201e968bffa757f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158919"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="c4cac-102">Método ICorRuntimeHost::CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="c4cac-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="c4cac-103">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4cac-103">Creates an application domain.</span></span> <span data-ttu-id="c4cac-104">O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain>, para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4cac-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4cac-105">Esse método permite que o chamador passe uma instância de IAppDomainSetup para configurar recursos adicionais do retornado <xref:System._AppDomain> instância.</span><span class="sxs-lookup"><span data-stu-id="c4cac-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4cac-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4cac-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4cac-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4cac-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="c4cac-108">[in] Um parâmetro opcional usado para dar um nome amigável no domínio.</span><span class="sxs-lookup"><span data-stu-id="c4cac-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="c4cac-109">Este nome amigável pode ser exibido nas interfaces do usuário, como depuradores para identificar o domínio.</span><span class="sxs-lookup"><span data-stu-id="c4cac-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="c4cac-110">[in] Um ponteiro de interface opcional do tipo `IAppDomainSetup`, obtida por uma chamada para o [icorruntimehost:: Createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c4cac-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="c4cac-111">[in] Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam a evidência mapeada por meio da política de segurança para estabelecer um conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="c4cac-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="c4cac-112">Uma `IIdentity` objeto pode ser obtido chamando o [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c4cac-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c4cac-113">[out] Um ponteiro de interface do tipo <xref:System._AppDomain> a uma instância de <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.</span><span class="sxs-lookup"><span data-stu-id="c4cac-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4cac-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c4cac-114">Return Value</span></span>  
  
|<span data-ttu-id="c4cac-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4cac-115">HRESULT</span></span>|<span data-ttu-id="c4cac-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4cac-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4cac-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4cac-117">S_OK</span></span>|<span data-ttu-id="c4cac-118">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c4cac-118">The operation was successful.</span></span>|  
|<span data-ttu-id="c4cac-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c4cac-119">S_FALSE</span></span>|<span data-ttu-id="c4cac-120">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="c4cac-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c4cac-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4cac-121">E_FAIL</span></span>|<span data-ttu-id="c4cac-122">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c4cac-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c4cac-123">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="c4cac-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c4cac-124">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4cac-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c4cac-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4cac-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4cac-126">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c4cac-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4cac-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4cac-127">Remarks</span></span>  
 <span data-ttu-id="c4cac-128">`CreateDomainEx` estende os recursos do [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) , permitindo que o chamador passe em um `IAppDomainSetup` instância com valores de propriedade para configurar o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4cac-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4cac-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4cac-129">Requirements</span></span>  
 <span data-ttu-id="c4cac-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4cac-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4cac-131">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4cac-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4cac-132">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c4cac-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4cac-133">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c4cac-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4cac-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4cac-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="c4cac-135">Método CreateDomain</span><span class="sxs-lookup"><span data-stu-id="c4cac-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="c4cac-136">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c4cac-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
