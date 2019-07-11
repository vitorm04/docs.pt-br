---
title: Método ICLRRuntimeHost::UnloadAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1a2358590b95b39b6495b74078f079c5b34876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765683"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="52d25-102">Método ICLRRuntimeHost::UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="52d25-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="52d25-103">Descarrega o gerenciado <xref:System.AppDomain> que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="52d25-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d25-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52d25-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52d25-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52d25-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="52d25-106">[in] O identificador numérico do domínio do aplicativo ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="52d25-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="52d25-107">[in] `true` para indicar que o common language runtime (CLR) deve esperar até que a execução do thread atual do aplicativo antes de tentar descarregar o domínio do aplicativo foi concluída.</span><span class="sxs-lookup"><span data-stu-id="52d25-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52d25-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="52d25-108">Return Value</span></span>  
  
|<span data-ttu-id="52d25-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52d25-109">HRESULT</span></span>|<span data-ttu-id="52d25-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="52d25-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52d25-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="52d25-111">S_OK</span></span>|<span data-ttu-id="52d25-112">`UnloadAppDomain` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="52d25-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="52d25-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52d25-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52d25-114">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="52d25-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52d25-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52d25-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52d25-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="52d25-116">The call timed out.</span></span>|  
|<span data-ttu-id="52d25-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52d25-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52d25-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="52d25-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52d25-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52d25-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52d25-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="52d25-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52d25-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52d25-121">E_FAIL</span></span>|<span data-ttu-id="52d25-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="52d25-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52d25-123">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="52d25-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52d25-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52d25-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52d25-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="52d25-125">Remarks</span></span>  
 <span data-ttu-id="52d25-126">Você pode obter o identificador numérico do domínio do aplicativo no qual o thread atual está em execução chamando [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="52d25-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="52d25-127">Esse identificador corresponde do <xref:System.AppDomain.Id%2A> propriedade de gerenciado <xref:System.AppDomain> tipo.</span><span class="sxs-lookup"><span data-stu-id="52d25-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52d25-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52d25-128">Requirements</span></span>  
 <span data-ttu-id="52d25-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52d25-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52d25-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52d25-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52d25-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="52d25-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52d25-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52d25-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d25-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52d25-133">See also</span></span>

- [<span data-ttu-id="52d25-134">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="52d25-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
