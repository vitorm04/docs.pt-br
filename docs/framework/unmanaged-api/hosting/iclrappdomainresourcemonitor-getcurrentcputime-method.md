---
title: Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d5149c7e3430c5e7c59a47c4ab5dc98d878de39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766671"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="ac8b1-102">Método ICLRAppDomainResourceMonitor::GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="ac8b1-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="ac8b1-103">Obtém o tempo total do processador que foi usado por todos os threads durante a execução no domínio do aplicativo atual, desde que o domínio do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac8b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac8b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac8b1-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="ac8b1-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="ac8b1-107">[out] Um ponteiro para o tempo total do processador que foi usado por todos os threads durante a execução no domínio do aplicativo atual desde que o domínio do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="ac8b1-108">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac8b1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac8b1-109">Return Value</span></span>  
  
|<span data-ttu-id="ac8b1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac8b1-110">HRESULT</span></span>|<span data-ttu-id="ac8b1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac8b1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac8b1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac8b1-112">S_OK</span></span>|<span data-ttu-id="ac8b1-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ac8b1-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="ac8b1-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="ac8b1-115">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="ac8b1-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac8b1-116">E_FAIL</span></span>|<span data-ttu-id="ac8b1-117">Monitoramento de recursos de domínio do aplicativo não está habilitado.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="ac8b1-118">- ou -</span><span class="sxs-lookup"><span data-stu-id="ac8b1-118">-or-</span></span><br /><br /> <span data-ttu-id="ac8b1-119">Todas as outras falhas.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac8b1-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac8b1-120">Remarks</span></span>  
 <span data-ttu-id="ac8b1-121">Esse método é não gerenciado equivalente gerenciado <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ac8b1-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac8b1-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac8b1-122">Requirements</span></span>  
 <span data-ttu-id="ac8b1-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac8b1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac8b1-124">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ac8b1-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ac8b1-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ac8b1-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac8b1-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac8b1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8b1-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac8b1-127">See also</span></span>

- [<span data-ttu-id="ac8b1-128">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="ac8b1-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="ac8b1-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ac8b1-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ac8b1-130">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ac8b1-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="ac8b1-131">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="ac8b1-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
