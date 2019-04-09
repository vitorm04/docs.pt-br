---
title: Método ICLRRuntimeHost::ExecuteInAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86348c35a023e22d10c4ad2e08f5cb1104b895a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165449"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="c7653-102">Método ICLRRuntimeHost::ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="c7653-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="c7653-103">Especifica o <xref:System.AppDomain> no qual executar o código gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="c7653-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7653-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7653-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7653-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7653-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="c7653-106">[in] A ID numérica da <xref:System.AppDomain> no qual executar o método especificado.</span><span class="sxs-lookup"><span data-stu-id="c7653-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="c7653-107">[in] Um ponteiro para a função a ser executada dentro do especificado <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c7653-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="c7653-108">[in] Um ponteiro opaco memória alocada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="c7653-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="c7653-109">Esse parâmetro é passado pelo common language runtime (CLR) para o retorno de chamada de domínio.</span><span class="sxs-lookup"><span data-stu-id="c7653-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="c7653-110">Não é memória de heap gerenciado pelo tempo de execução; tempo de vida da memória e alocação são controlados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="c7653-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7653-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c7653-111">Return Value</span></span>  
  
|<span data-ttu-id="c7653-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7653-112">HRESULT</span></span>|<span data-ttu-id="c7653-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7653-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7653-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7653-114">S_OK</span></span>|`ExecuteInAppDomain` <span data-ttu-id="c7653-115">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="c7653-115">returned successfully.</span></span>|  
|<span data-ttu-id="c7653-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7653-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7653-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c7653-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7653-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7653-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7653-119">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c7653-119">The call timed out.</span></span>|  
|<span data-ttu-id="c7653-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7653-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7653-121">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c7653-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7653-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7653-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7653-123">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="c7653-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7653-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7653-124">E_FAIL</span></span>|<span data-ttu-id="c7653-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="c7653-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7653-126">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="c7653-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7653-127">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c7653-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7653-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7653-128">Remarks</span></span>  
 `ExecuteInAppDomain` <span data-ttu-id="c7653-129">permite que o host exercer controle sobre quais gerenciados <xref:System.AppDomain> o método gerenciado especificado deve ser executado no.</span><span class="sxs-lookup"><span data-stu-id="c7653-129">allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="c7653-130">Você pode obter o valor do identificador do domínio de aplicativo, que corresponde ao valor de <xref:System.AppDomain.Id%2A> propriedade chamando [método GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7653-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7653-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7653-131">Requirements</span></span>  
 <span data-ttu-id="c7653-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7653-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7653-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7653-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7653-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c7653-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c7653-135">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c7653-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7653-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7653-136">See also</span></span>

- [<span data-ttu-id="c7653-137">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c7653-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
