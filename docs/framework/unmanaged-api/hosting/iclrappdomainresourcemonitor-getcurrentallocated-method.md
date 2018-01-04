---
title: "Método ICLRAppDomainResourceMonitor::GetCurrentAllocated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2b69f2f8e8273c07d277ff7460ad977fade89ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="60691-102">Método ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="60691-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="60691-103">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="60691-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60691-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60691-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60691-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60691-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="60691-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="60691-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="60691-107">[out] Um ponteiro para o tamanho total de todas as alocações de memória.</span><span class="sxs-lookup"><span data-stu-id="60691-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60691-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="60691-108">Return Value</span></span>  
 <span data-ttu-id="60691-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="60691-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="60691-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60691-110">HRESULT</span></span>|<span data-ttu-id="60691-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="60691-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60691-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="60691-112">S_OK</span></span>|<span data-ttu-id="60691-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="60691-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="60691-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="60691-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="60691-115">O domínio de aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="60691-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60691-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="60691-116">Remarks</span></span>  
 <span data-ttu-id="60691-117">Esse método é o equivalente não gerenciado a gerenciado <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="60691-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60691-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60691-118">Requirements</span></span>  
 <span data-ttu-id="60691-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60691-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60691-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="60691-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="60691-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="60691-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60691-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60691-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60691-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60691-123">See Also</span></span>  
 [<span data-ttu-id="60691-124">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="60691-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="60691-125">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="60691-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="60691-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="60691-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="60691-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="60691-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
