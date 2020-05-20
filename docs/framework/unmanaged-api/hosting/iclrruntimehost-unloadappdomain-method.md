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
ms.openlocfilehash: 293c1764f4c0d857138726b8ed4855b1e3b03116
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703927"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="834a9-102">Método ICLRRuntimeHost::UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="834a9-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="834a9-103">Descarrega o gerenciado <xref:System.AppDomain> que corresponde ao identificador numérico especificado.</span><span class="sxs-lookup"><span data-stu-id="834a9-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="834a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="834a9-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="834a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="834a9-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="834a9-106">no O identificador numérico do domínio do aplicativo a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="834a9-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="834a9-107">[in] `true` para indicar que o Common Language Runtime (CLR) deve aguardar até concluir a execução do thread atual do aplicativo antes de tentar descarregar o domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="834a9-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="834a9-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="834a9-108">Return Value</span></span>  
  
|<span data-ttu-id="834a9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="834a9-109">HRESULT</span></span>|<span data-ttu-id="834a9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="834a9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="834a9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="834a9-111">S_OK</span></span>|<span data-ttu-id="834a9-112">`UnloadAppDomain`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="834a9-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="834a9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="834a9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="834a9-114">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="834a9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="834a9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="834a9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="834a9-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="834a9-116">The call timed out.</span></span>|  
|<span data-ttu-id="834a9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="834a9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="834a9-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="834a9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="834a9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="834a9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="834a9-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="834a9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="834a9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="834a9-121">E_FAIL</span></span>|<span data-ttu-id="834a9-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="834a9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="834a9-123">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="834a9-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="834a9-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="834a9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="834a9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="834a9-125">Remarks</span></span>  
 <span data-ttu-id="834a9-126">Você pode obter o identificador numérico do domínio do aplicativo no qual o thread atual está sendo executado chamando [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="834a9-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="834a9-127">Esse identificador corresponde à <xref:System.AppDomain.Id%2A> Propriedade do <xref:System.AppDomain> tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="834a9-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="834a9-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="834a9-128">Requirements</span></span>  
 <span data-ttu-id="834a9-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="834a9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="834a9-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="834a9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="834a9-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="834a9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="834a9-132">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="834a9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834a9-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="834a9-133">See also</span></span>

- [<span data-ttu-id="834a9-134">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="834a9-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
