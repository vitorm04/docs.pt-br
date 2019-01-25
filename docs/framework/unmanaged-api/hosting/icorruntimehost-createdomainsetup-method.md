---
title: Método ICorRuntimeHost::CreateDomainSetup
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ab00a93b0bedb8f7ea1425c65c4940b57f11219
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591573"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="ba22c-102">Método ICorRuntimeHost::CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="ba22c-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="ba22c-103">Obtém um ponteiro de interface do tipo IAppDomainSetup para um <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="ba22c-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="ba22c-104">`IAppDomainSetup` fornece métodos para configurar aspectos de um domínio do aplicativo antes de ele é criado.</span><span class="sxs-lookup"><span data-stu-id="ba22c-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba22c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba22c-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba22c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba22c-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="ba22c-107">[out] Um ponteiro de interface para um <xref:System.AppDomainSetup?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="ba22c-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="ba22c-108">Esse parâmetro é digitado como `IUnknown`, de modo que os chamadores devem chamar geralmente `QueryInterface` nesse ponteiro para obter um ponteiro de interface do tipo `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="ba22c-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba22c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ba22c-109">Return Value</span></span>  
  
|<span data-ttu-id="ba22c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba22c-110">HRESULT</span></span>|<span data-ttu-id="ba22c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba22c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba22c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba22c-112">S_OK</span></span>|<span data-ttu-id="ba22c-113">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ba22c-113">The operation was successful.</span></span>|  
|<span data-ttu-id="ba22c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ba22c-114">S_FALSE</span></span>|<span data-ttu-id="ba22c-115">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="ba22c-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ba22c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba22c-116">E_FAIL</span></span>|<span data-ttu-id="ba22c-117">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ba22c-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ba22c-118">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ba22c-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ba22c-119">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ba22c-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ba22c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba22c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba22c-121">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ba22c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba22c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba22c-122">Remarks</span></span>  
 <span data-ttu-id="ba22c-123">O ponteiro retornado desse método é normalmente passado como um parâmetro para o [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ba22c-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba22c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba22c-124">Requirements</span></span>  
 <span data-ttu-id="ba22c-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba22c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba22c-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba22c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba22c-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ba22c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba22c-128">**Versão do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ba22c-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba22c-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba22c-129">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="ba22c-130">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ba22c-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
