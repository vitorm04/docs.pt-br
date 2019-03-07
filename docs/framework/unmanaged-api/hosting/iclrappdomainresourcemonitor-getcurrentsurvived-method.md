---
title: Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a24f51884b5dc55e45d22f33735fe07db770d06
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466898"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="5c519-102">Método ICLRAppDomainResourceMonitor::GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="5c519-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="5c519-103">Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="5c519-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c519-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c519-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c519-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c519-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="5c519-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="5c519-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="5c519-107">[out] Um ponteiro para o número de bytes que sobreviveram após a última coleta de lixo que são mantidos por esse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c519-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="5c519-108">Após uma coleta completa, esse número é preciso e completo.</span><span class="sxs-lookup"><span data-stu-id="5c519-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="5c519-109">Após uma coleta efêmera, esse número é potencialmente incompleto.</span><span class="sxs-lookup"><span data-stu-id="5c519-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="5c519-110">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="5c519-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="5c519-111">[out] Um ponteiro para o número total de bytes que sobreviveram da última coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5c519-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="5c519-112">Após uma coleta completa, esse número representa o número de bytes que são mantidos em heaps gerenciados.</span><span class="sxs-lookup"><span data-stu-id="5c519-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="5c519-113">Após uma coleta efêmera, esse número representa o número de bytes que são mantidos ativos em gerações efêmeras.</span><span class="sxs-lookup"><span data-stu-id="5c519-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="5c519-114">Esse parâmetro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="5c519-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c519-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c519-115">Return Value</span></span>  
 <span data-ttu-id="5c519-116">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="5c519-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5c519-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c519-117">HRESULT</span></span>|<span data-ttu-id="5c519-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c519-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c519-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c519-119">S_OK</span></span>|<span data-ttu-id="5c519-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="5c519-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="5c519-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="5c519-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="5c519-122">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="5c519-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c519-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c519-123">Remarks</span></span>  
 <span data-ttu-id="5c519-124">As estatísticas são atualizadas somente depois de completa, o bloqueio de coleta de lixo; ou seja, uma coleção que inclui todas as gerações e que interrompe o aplicativo durante a coleta ocorre.</span><span class="sxs-lookup"><span data-stu-id="5c519-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="5c519-125">Por exemplo, o <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método executa uma completa de coleta de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5c519-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="5c519-126">Coleta de lixo simultânea ocorre em segundo plano e não bloqueia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c519-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="5c519-127">O `GetCurrentSurvived` método é não gerenciado equivalente gerenciado <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5c519-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c519-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c519-128">Requirements</span></span>  
 <span data-ttu-id="5c519-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c519-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c519-130">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5c519-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c519-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5c519-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c519-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c519-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c519-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c519-133">See also</span></span>
- [<span data-ttu-id="5c519-134">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="5c519-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="5c519-135">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5c519-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="5c519-136">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="5c519-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5c519-137">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5c519-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
