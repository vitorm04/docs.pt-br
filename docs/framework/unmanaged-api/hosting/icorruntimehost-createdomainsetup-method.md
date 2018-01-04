---
title: "Método ICorRuntimeHost::CreateDomainSetup"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e15f40402b222037f7ed8b23be3df36acafc73c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="dee7f-102">Método ICorRuntimeHost::CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="dee7f-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="dee7f-103">Obtém um ponteiro de interface do tipo IAppDomainSetup para um <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="dee7f-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="dee7f-104">`IAppDomainSetup`fornece métodos para configurar aspectos de um domínio de aplicativo antes que ele é criado.</span><span class="sxs-lookup"><span data-stu-id="dee7f-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee7f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dee7f-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dee7f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dee7f-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="dee7f-107">[out] Um ponteiro de interface para um <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="dee7f-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="dee7f-108">Esse parâmetro é digitado como `IUnknown`, de modo que os chamadores devem chamar geralmente `QueryInterface` esse ponteiro para obter um ponteiro de interface do tipo `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="dee7f-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dee7f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dee7f-109">Return Value</span></span>  
  
|<span data-ttu-id="dee7f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dee7f-110">HRESULT</span></span>|<span data-ttu-id="dee7f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee7f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dee7f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dee7f-112">S_OK</span></span>|<span data-ttu-id="dee7f-113">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="dee7f-113">The operation was successful.</span></span>|  
|<span data-ttu-id="dee7f-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dee7f-114">S_FALSE</span></span>|<span data-ttu-id="dee7f-115">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="dee7f-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="dee7f-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dee7f-116">E_FAIL</span></span>|<span data-ttu-id="dee7f-117">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dee7f-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dee7f-118">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="dee7f-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="dee7f-119">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dee7f-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dee7f-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dee7f-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dee7f-121">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dee7f-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee7f-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="dee7f-122">Remarks</span></span>  
 <span data-ttu-id="dee7f-123">O ponteiro retornado deste método geralmente é passado como um parâmetro para o [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="dee7f-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee7f-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dee7f-124">Requirements</span></span>  
 <span data-ttu-id="dee7f-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee7f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee7f-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dee7f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dee7f-127">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dee7f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dee7f-128">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="dee7f-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee7f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dee7f-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="dee7f-130">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dee7f-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
