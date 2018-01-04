---
title: "Método ICLRRuntimeHost::ExecuteInAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c540c9618655e6df30ad253e0c4cccdf6624e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="a31d6-102">Método ICLRRuntimeHost::ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="a31d6-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="a31d6-103">Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="a31d6-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a31d6-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a31d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a31d6-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="a31d6-106">[in] A ID numérica do <xref:System.AppDomain> no qual executar o método especificado.</span><span class="sxs-lookup"><span data-stu-id="a31d6-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="a31d6-107">[in] Um ponteiro para a função a ser executada no especificado <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a31d6-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="a31d6-108">[in] Um ponteiro para a memória alocada pelo chamador de opaco.</span><span class="sxs-lookup"><span data-stu-id="a31d6-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="a31d6-109">Este parâmetro é passado pelo common language runtime (CLR) para o retorno de chamada do domínio.</span><span class="sxs-lookup"><span data-stu-id="a31d6-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="a31d6-110">Não é memória de heap gerenciado em tempo de execução. a alocação e o tempo de vida da memória são controladas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="a31d6-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a31d6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a31d6-111">Return Value</span></span>  
  
|<span data-ttu-id="a31d6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a31d6-112">HRESULT</span></span>|<span data-ttu-id="a31d6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a31d6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a31d6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a31d6-114">S_OK</span></span>|<span data-ttu-id="a31d6-115">`ExecuteInAppDomain`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a31d6-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="a31d6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a31d6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a31d6-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a31d6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a31d6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a31d6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a31d6-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a31d6-119">The call timed out.</span></span>|  
|<span data-ttu-id="a31d6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a31d6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a31d6-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a31d6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a31d6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a31d6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a31d6-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a31d6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a31d6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a31d6-124">E_FAIL</span></span>|<span data-ttu-id="a31d6-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a31d6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a31d6-126">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a31d6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a31d6-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a31d6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a31d6-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a31d6-128">Remarks</span></span>  
 <span data-ttu-id="a31d6-129">`ExecuteInAppDomain`permite que o host exercer controle sobre qual gerenciado <xref:System.AppDomain> o método gerenciado especificado deve ser executado no.</span><span class="sxs-lookup"><span data-stu-id="a31d6-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="a31d6-130">Você pode obter o valor do identificador de um domínio aplicativo, que corresponde ao valor da <xref:System.AppDomain.Id%2A> propriedade chamando [método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="a31d6-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a31d6-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a31d6-131">Requirements</span></span>  
 <span data-ttu-id="a31d6-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a31d6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a31d6-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a31d6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a31d6-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a31d6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a31d6-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31d6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31d6-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a31d6-136">See Also</span></span>  
 [<span data-ttu-id="a31d6-137">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a31d6-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
