---
title: Método ICLRControl::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eacd3802c51cb6ccf3f7ba874c75a2d2774439d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091181"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="6d19c-102">Método ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="6d19c-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="6d19c-103">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6d19c-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d19c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d19c-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d19c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d19c-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="6d19c-106">[in] O nome do assembly no qual o tipo solicitado derivado <xref:System.AppDomainManager> é implementado.</span><span class="sxs-lookup"><span data-stu-id="6d19c-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="6d19c-107">[in] O nome do tipo implementado de `pwzAppDomainManagerAssembly` parâmetro que implementa os recursos do <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="6d19c-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d19c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6d19c-108">Return Value</span></span>  
  
|<span data-ttu-id="6d19c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d19c-109">HRESULT</span></span>|<span data-ttu-id="6d19c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d19c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d19c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d19c-111">S_OK</span></span>|<span data-ttu-id="6d19c-112">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6d19c-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="6d19c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d19c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d19c-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6d19c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d19c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d19c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d19c-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6d19c-116">The call timed out.</span></span>|  
|<span data-ttu-id="6d19c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d19c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d19c-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6d19c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d19c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d19c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d19c-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="6d19c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d19c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d19c-121">E_FAIL</span></span>|<span data-ttu-id="6d19c-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6d19c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d19c-123">Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="6d19c-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d19c-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6d19c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d19c-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d19c-125">Requirements</span></span>  
 <span data-ttu-id="6d19c-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d19c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d19c-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d19c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d19c-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6d19c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6d19c-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6d19c-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d19c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d19c-130">See also</span></span>

- [<span data-ttu-id="6d19c-131">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6d19c-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6d19c-132">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="6d19c-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
