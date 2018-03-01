---
title: "Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2781cfb1e23db02ab8192c78bd0a3e585ee28b2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="f4815-102">Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="f4815-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="f4815-103">Obtém o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual, desde que o domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="f4815-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4815-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4815-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4815-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4815-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="f4815-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="f4815-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="f4815-107">[out] Um ponteiro para o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual desde que o domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="f4815-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="f4815-108">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f4815-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4815-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f4815-109">Return Value</span></span>  
  
|<span data-ttu-id="f4815-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4815-110">HRESULT</span></span>|<span data-ttu-id="f4815-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4815-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4815-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4815-112">S_OK</span></span>|<span data-ttu-id="f4815-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f4815-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f4815-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="f4815-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="f4815-115">O domínio de aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="f4815-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="f4815-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4815-116">E_FAIL</span></span>|<span data-ttu-id="f4815-117">Monitoramento de recursos do domínio de aplicativo não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="f4815-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="f4815-118">-ou-</span><span class="sxs-lookup"><span data-stu-id="f4815-118">-or-</span></span><br /><br /> <span data-ttu-id="f4815-119">Todas as outras falhas.</span><span class="sxs-lookup"><span data-stu-id="f4815-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4815-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="f4815-120">Remarks</span></span>  
 <span data-ttu-id="f4815-121">Esse método é o equivalente não gerenciado a gerenciado <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f4815-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4815-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4815-122">Requirements</span></span>  
 <span data-ttu-id="f4815-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4815-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4815-124">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f4815-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f4815-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f4815-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4815-126">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4815-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4815-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4815-127">See Also</span></span>  
 [<span data-ttu-id="f4815-128">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="f4815-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="f4815-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f4815-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f4815-130">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f4815-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="f4815-131">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="f4815-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
