---
title: Método ICLRRuntimeHost::GetCurrentAppDomainId
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 1b7d321eec2bbc2beb47c5de034bb4ef5d534c9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120462"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="e799b-102">Método ICLRRuntimeHost::GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="e799b-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="e799b-103">Obtém o identificador numérico do <xref:System.AppDomain> que está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="e799b-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e799b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e799b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e799b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e799b-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="e799b-106">fora O identificador numérico do <xref:System.AppDomain> que está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="e799b-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e799b-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e799b-107">Return Value</span></span>  
  
|<span data-ttu-id="e799b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e799b-108">HRESULT</span></span>|<span data-ttu-id="e799b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e799b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e799b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e799b-110">S_OK</span></span>|<span data-ttu-id="e799b-111">`GetCurrentAppDomainId` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e799b-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="e799b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e799b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e799b-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e799b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e799b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e799b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e799b-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e799b-115">The call timed out.</span></span>|  
|<span data-ttu-id="e799b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e799b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e799b-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e799b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e799b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e799b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e799b-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e799b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e799b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e799b-120">E_FAIL</span></span>|<span data-ttu-id="e799b-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e799b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e799b-122">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="e799b-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e799b-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e799b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e799b-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e799b-124">Remarks</span></span>  
 <span data-ttu-id="e799b-125">O parâmetro `pdwAppDomainId` é definido como o valor da propriedade <xref:System.AppDomain.Id%2A> do <xref:System.AppDomain> no qual o thread atual está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="e799b-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e799b-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e799b-126">Requirements</span></span>  
 <span data-ttu-id="e799b-127">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e799b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e799b-128">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e799b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e799b-129">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e799b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e799b-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e799b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e799b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e799b-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="e799b-132">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e799b-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
