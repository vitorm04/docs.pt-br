---
title: Método ICLRAppDomainResourceMonitor::GetCurrentAllocated
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fcd7a3aa1a6c034985099c24071429384563700
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129383"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="861d8-102">Método ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="861d8-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="861d8-103">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo, pois ele foi criado, sem subtrair a memória que foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="861d8-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="861d8-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="861d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="861d8-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="861d8-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="861d8-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="861d8-107">[out] Um ponteiro para o tamanho total de todas as alocações de memória.</span><span class="sxs-lookup"><span data-stu-id="861d8-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="861d8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="861d8-108">Return Value</span></span>  
 <span data-ttu-id="861d8-109">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="861d8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="861d8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="861d8-110">HRESULT</span></span>|<span data-ttu-id="861d8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="861d8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="861d8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="861d8-112">S_OK</span></span>|<span data-ttu-id="861d8-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="861d8-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="861d8-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="861d8-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="861d8-115">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="861d8-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="861d8-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="861d8-116">Remarks</span></span>  
 <span data-ttu-id="861d8-117">Esse método é não gerenciado equivalente gerenciado <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="861d8-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="861d8-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="861d8-118">Requirements</span></span>  
 <span data-ttu-id="861d8-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="861d8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="861d8-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="861d8-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="861d8-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="861d8-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="861d8-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="861d8-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="861d8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="861d8-123">See also</span></span>

- [<span data-ttu-id="861d8-124">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="861d8-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="861d8-125">Monitoramento de recursos de domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="861d8-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="861d8-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="861d8-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="861d8-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="861d8-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
