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
ms.openlocfilehash: e62f9fd6b8421ea131eff0e6b36523718589c921
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615820"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="907ed-102">Método ICLRControl::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="907ed-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="907ed-103">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="907ed-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="907ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="907ed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="907ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="907ed-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="907ed-106">no O nome do assembly no qual o tipo solicitado derivado <xref:System.AppDomainManager> é implementado.</span><span class="sxs-lookup"><span data-stu-id="907ed-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="907ed-107">no O nome do tipo implementado no `pwzAppDomainManagerAssembly` parâmetro que implementa os recursos do <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="907ed-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="907ed-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="907ed-108">Return Value</span></span>  
  
|<span data-ttu-id="907ed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="907ed-109">HRESULT</span></span>|<span data-ttu-id="907ed-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="907ed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="907ed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="907ed-111">S_OK</span></span>|<span data-ttu-id="907ed-112">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="907ed-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="907ed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="907ed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="907ed-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="907ed-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="907ed-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="907ed-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="907ed-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="907ed-116">The call timed out.</span></span>|  
|<span data-ttu-id="907ed-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="907ed-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="907ed-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="907ed-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="907ed-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="907ed-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="907ed-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="907ed-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="907ed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="907ed-121">E_FAIL</span></span>|<span data-ttu-id="907ed-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="907ed-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="907ed-123">Depois que um método retorna E_FAIL, o CLR não pode mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="907ed-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="907ed-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="907ed-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="907ed-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="907ed-125">Requirements</span></span>  
 <span data-ttu-id="907ed-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="907ed-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="907ed-127">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="907ed-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="907ed-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="907ed-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="907ed-129">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="907ed-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907ed-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="907ed-130">See also</span></span>

- [<span data-ttu-id="907ed-131">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="907ed-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="907ed-132">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="907ed-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)
