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
ms.openlocfilehash: be29a4f83901b8e8fc338c2daa8f5703523402b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126582"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="86289-102">Método ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="86289-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="86289-103">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86289-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86289-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86289-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86289-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86289-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="86289-106">no O nome do assembly no qual o tipo solicitado derivado de <xref:System.AppDomainManager> é implementado.</span><span class="sxs-lookup"><span data-stu-id="86289-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="86289-107">no O nome do tipo implementado no parâmetro `pwzAppDomainManagerAssembly` que implementa os recursos de <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="86289-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86289-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="86289-108">Return Value</span></span>  
  
|<span data-ttu-id="86289-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86289-109">HRESULT</span></span>|<span data-ttu-id="86289-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="86289-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86289-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86289-111">S_OK</span></span>|<span data-ttu-id="86289-112">O método retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="86289-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="86289-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86289-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86289-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="86289-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86289-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86289-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86289-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="86289-116">The call timed out.</span></span>|  
|<span data-ttu-id="86289-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86289-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86289-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="86289-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86289-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86289-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86289-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="86289-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86289-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86289-121">E_FAIL</span></span>|<span data-ttu-id="86289-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="86289-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86289-123">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="86289-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86289-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86289-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86289-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86289-125">Requirements</span></span>  
 <span data-ttu-id="86289-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86289-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86289-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86289-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86289-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86289-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86289-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86289-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86289-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86289-130">See also</span></span>

- [<span data-ttu-id="86289-131">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="86289-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="86289-132">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="86289-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
