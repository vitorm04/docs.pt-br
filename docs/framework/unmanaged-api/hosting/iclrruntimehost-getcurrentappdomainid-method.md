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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82096f790befbab58a1d27978be553aae2190b5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496359"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="1b5b0-102">Método ICLRRuntimeHost::GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="1b5b0-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="1b5b0-103">Obtém o identificador numérico do <xref:System.AppDomain> que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b5b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b5b0-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b5b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b5b0-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="1b5b0-106">[out] O identificador numérico do <xref:System.AppDomain> que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b5b0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1b5b0-107">Return Value</span></span>  
  
|<span data-ttu-id="1b5b0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b5b0-108">HRESULT</span></span>|<span data-ttu-id="1b5b0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b5b0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b5b0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b5b0-110">S_OK</span></span>|<span data-ttu-id="1b5b0-111">`GetCurrentAppDomainId` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="1b5b0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b5b0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b5b0-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b5b0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b5b0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b5b0-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b5b0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b5b0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b5b0-117">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b5b0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b5b0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b5b0-119">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b5b0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b5b0-120">E_FAIL</span></span>|<span data-ttu-id="1b5b0-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b5b0-122">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b5b0-123">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b5b0-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b5b0-124">Remarks</span></span>  
 <span data-ttu-id="1b5b0-125">O `pdwAppDomainId` parâmetro é definido como o valor da <xref:System.AppDomain.Id%2A> propriedade do <xref:System.AppDomain> no qual o thread atual está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1b5b0-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b5b0-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b5b0-126">Requirements</span></span>  
 <span data-ttu-id="1b5b0-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b5b0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b5b0-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b5b0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b5b0-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1b5b0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b5b0-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5b0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b5b0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b5b0-131">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="1b5b0-132">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1b5b0-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
