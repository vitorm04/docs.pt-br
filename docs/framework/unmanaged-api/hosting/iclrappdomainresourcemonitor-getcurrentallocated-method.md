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
ms.openlocfilehash: 7d02478c2421823ce2acb533d2abea2ea8b13c74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950285"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="db37a-102">Método ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="db37a-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="db37a-103">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória que foi coletada por lixo.</span><span class="sxs-lookup"><span data-stu-id="db37a-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db37a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db37a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db37a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db37a-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="db37a-106">no A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="db37a-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="db37a-107">fora Um ponteiro para o tamanho total de todas as alocações de memória.</span><span class="sxs-lookup"><span data-stu-id="db37a-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db37a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db37a-108">Return Value</span></span>  
 <span data-ttu-id="db37a-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="db37a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="db37a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db37a-110">HRESULT</span></span>|<span data-ttu-id="db37a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="db37a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db37a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="db37a-112">S_OK</span></span>|<span data-ttu-id="db37a-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="db37a-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="db37a-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="db37a-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="db37a-115">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="db37a-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db37a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="db37a-116">Remarks</span></span>  
 <span data-ttu-id="db37a-117">Esse método é o equivalente não gerenciado da propriedade gerenciada <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="db37a-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db37a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db37a-118">Requirements</span></span>  
 <span data-ttu-id="db37a-119">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db37a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db37a-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db37a-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db37a-121">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db37a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db37a-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db37a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db37a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db37a-123">See also</span></span>

- [<span data-ttu-id="db37a-124">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="db37a-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="db37a-125">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="db37a-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="db37a-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="db37a-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="db37a-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="db37a-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
