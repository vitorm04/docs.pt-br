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
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762338"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="a14d7-102">Método ICorRuntimeHost::CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="a14d7-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="a14d7-103">Cria um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a14d7-103">Creates an application domain.</span></span> <span data-ttu-id="a14d7-104">O chamador recebe um ponteiro de interface, do tipo <xref:System._AppDomain> , para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a14d7-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a14d7-105">Esse método permite que o chamador passe uma instância de IAppDomainSetup para configurar recursos adicionais da <xref:System._AppDomain> instância retornada.</span><span class="sxs-lookup"><span data-stu-id="a14d7-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14d7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a14d7-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a14d7-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a14d7-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="a14d7-108">no Um parâmetro opcional usado para fornecer um nome amigável ao domínio.</span><span class="sxs-lookup"><span data-stu-id="a14d7-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="a14d7-109">Esse nome amigável pode ser exibido em interfaces do usuário, como depuradores, para identificar o domínio.</span><span class="sxs-lookup"><span data-stu-id="a14d7-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="a14d7-110">no Um ponteiro de interface opcional do tipo `IAppDomainSetup` , obtido por uma chamada para o método [ICorRuntimeHost:: CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a14d7-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="a14d7-111">no Uma matriz opcional de ponteiros para `IIdentity` instâncias que representam evidências mapeadas pela política de segurança para estabelecer um conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="a14d7-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="a14d7-112">Um `IIdentity` objeto pode ser obtido chamando o método [CreateEvidence](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a14d7-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a14d7-113">fora Um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do <xref:System.AppDomain?displayProperty=nameWithType> que pode ser usado para controlar ainda mais o domínio.</span><span class="sxs-lookup"><span data-stu-id="a14d7-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a14d7-114">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a14d7-114">Return Value</span></span>  
  
|<span data-ttu-id="a14d7-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a14d7-115">HRESULT</span></span>|<span data-ttu-id="a14d7-116">Description</span><span class="sxs-lookup"><span data-stu-id="a14d7-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a14d7-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="a14d7-117">S_OK</span></span>|<span data-ttu-id="a14d7-118">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a14d7-118">The operation was successful.</span></span>|  
|<span data-ttu-id="a14d7-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a14d7-119">S_FALSE</span></span>|<span data-ttu-id="a14d7-120">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="a14d7-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a14d7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a14d7-121">E_FAIL</span></span>|<span data-ttu-id="a14d7-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a14d7-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a14d7-123">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="a14d7-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a14d7-124">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a14d7-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a14d7-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a14d7-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a14d7-126">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a14d7-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a14d7-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="a14d7-127">Remarks</span></span>  
 <span data-ttu-id="a14d7-128">`CreateDomainEx`estende os recursos do [CreateDomain](icorruntimehost-createdomain-method.md) permitindo que o chamador passe em uma `IAppDomainSetup` instância com valores de propriedade para configurar o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a14d7-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a14d7-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a14d7-129">Requirements</span></span>  
 <span data-ttu-id="a14d7-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a14d7-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a14d7-131">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a14d7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a14d7-132">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a14d7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a14d7-133">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a14d7-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14d7-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="a14d7-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="a14d7-135">Método CreateDomain</span><span class="sxs-lookup"><span data-stu-id="a14d7-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="a14d7-136">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a14d7-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
