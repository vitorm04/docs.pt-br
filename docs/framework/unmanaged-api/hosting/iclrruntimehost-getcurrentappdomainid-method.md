---
title: "Método ICLRRuntimeHost::GetCurrentAppDomainId"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCurrentAppDomainId
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e4e682ae71512e24d91ea7e4e12a8a2dd70f1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="77a29-102">Método ICLRRuntimeHost::GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="77a29-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="77a29-103">Obtém o identificador numérico do <xref:System.AppDomain> que está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="77a29-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77a29-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77a29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77a29-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="77a29-106">[out] O identificador numérico do <xref:System.AppDomain> que está em execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="77a29-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77a29-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="77a29-107">Return Value</span></span>  
  
|<span data-ttu-id="77a29-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77a29-108">HRESULT</span></span>|<span data-ttu-id="77a29-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="77a29-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77a29-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="77a29-110">S_OK</span></span>|<span data-ttu-id="77a29-111">`GetCurrentAppDomainId`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="77a29-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="77a29-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77a29-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77a29-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="77a29-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77a29-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77a29-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77a29-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="77a29-115">The call timed out.</span></span>|  
|<span data-ttu-id="77a29-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77a29-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77a29-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="77a29-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77a29-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77a29-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77a29-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="77a29-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77a29-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77a29-120">E_FAIL</span></span>|<span data-ttu-id="77a29-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="77a29-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77a29-122">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="77a29-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77a29-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77a29-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77a29-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="77a29-124">Remarks</span></span>  
 <span data-ttu-id="77a29-125">O `pdwAppDomainId` parâmetro está definido como o valor da <xref:System.AppDomain.Id%2A> propriedade o <xref:System.AppDomain> no qual o thread atual está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="77a29-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a29-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77a29-126">Requirements</span></span>  
 <span data-ttu-id="77a29-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a29-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a29-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77a29-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77a29-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="77a29-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77a29-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a29-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a29-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77a29-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="77a29-132">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="77a29-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
