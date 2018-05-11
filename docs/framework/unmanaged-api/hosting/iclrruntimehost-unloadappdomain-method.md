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
ms.openlocfilehash: c7dba595953a305c9da33e255676c4b2dcae7a96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="1dcb0-102">Método ICLRRuntimeHost::UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="1dcb0-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="1dcb0-103">Descarrega o gerenciado <xref:System.AppDomain> que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcb0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1dcb0-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dcb0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1dcb0-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="1dcb0-106">[in] O identificador numérico do domínio do aplicativo ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="1dcb0-107">[in] `true` para indicar que o common language runtime (CLR) deve esperar até que ele tiver concluído a execução do thread atual do aplicativo antes de tentar descarregar o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dcb0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1dcb0-108">Return Value</span></span>  
  
|<span data-ttu-id="1dcb0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1dcb0-109">HRESULT</span></span>|<span data-ttu-id="1dcb0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1dcb0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1dcb0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1dcb0-111">S_OK</span></span>|<span data-ttu-id="1dcb0-112">`UnloadAppDomain` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="1dcb0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1dcb0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1dcb0-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1dcb0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1dcb0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1dcb0-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-116">The call timed out.</span></span>|  
|<span data-ttu-id="1dcb0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1dcb0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1dcb0-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1dcb0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1dcb0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1dcb0-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1dcb0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1dcb0-121">E_FAIL</span></span>|<span data-ttu-id="1dcb0-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1dcb0-123">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1dcb0-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dcb0-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dcb0-125">Remarks</span></span>  
 <span data-ttu-id="1dcb0-126">Você pode obter o identificador numérico do domínio do aplicativo no qual o thread atual está em execução chamando [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="1dcb0-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="1dcb0-127">Esse identificador corresponde do <xref:System.AppDomain.Id%2A> propriedade gerenciada <xref:System.AppDomain> tipo.</span><span class="sxs-lookup"><span data-stu-id="1dcb0-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dcb0-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1dcb0-128">Requirements</span></span>  
 <span data-ttu-id="1dcb0-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dcb0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcb0-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1dcb0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dcb0-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1dcb0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dcb0-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcb0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcb0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dcb0-133">See Also</span></span>  
 [<span data-ttu-id="1dcb0-134">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1dcb0-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
