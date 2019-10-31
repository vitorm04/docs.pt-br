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
ms.openlocfilehash: 2a6dc878f156d5d18970fed72c9722bab60f9ba8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120401"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="dd1a6-102">Método ICLRRuntimeHost::UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="dd1a6-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="dd1a6-103">Descarrega o <xref:System.AppDomain> gerenciado que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd1a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd1a6-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd1a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd1a6-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="dd1a6-106">no O identificador numérico do domínio do aplicativo a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="dd1a6-107">[in] `true` para indicar que o Common Language Runtime (CLR) deve aguardar até concluir a execução do thread atual do aplicativo antes de tentar descarregar o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd1a6-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dd1a6-108">Return Value</span></span>  
  
|<span data-ttu-id="dd1a6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd1a6-109">HRESULT</span></span>|<span data-ttu-id="dd1a6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd1a6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd1a6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd1a6-111">S_OK</span></span>|<span data-ttu-id="dd1a6-112">`UnloadAppDomain` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="dd1a6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd1a6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd1a6-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd1a6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd1a6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd1a6-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-116">The call timed out.</span></span>|  
|<span data-ttu-id="dd1a6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd1a6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd1a6-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd1a6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd1a6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd1a6-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd1a6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd1a6-121">E_FAIL</span></span>|<span data-ttu-id="dd1a6-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd1a6-123">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd1a6-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd1a6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd1a6-125">Remarks</span></span>  
 <span data-ttu-id="dd1a6-126">Você pode obter o identificador numérico do domínio do aplicativo no qual o thread atual está sendo executado chamando [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd1a6-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="dd1a6-127">Esse identificador corresponde à propriedade <xref:System.AppDomain.Id%2A> do tipo de <xref:System.AppDomain> gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dd1a6-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd1a6-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd1a6-128">Requirements</span></span>  
 <span data-ttu-id="dd1a6-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd1a6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd1a6-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd1a6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd1a6-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd1a6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd1a6-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd1a6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1a6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd1a6-133">See also</span></span>

- [<span data-ttu-id="dd1a6-134">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd1a6-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
