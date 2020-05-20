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
ms.openlocfilehash: 685d303b31b8f8c20cbbdb8aec6fc127650aa32a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616041"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="0b8ba-102">Método ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="0b8ba-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="0b8ba-103">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória que foi coletada por lixo.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b8ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b8ba-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="0b8ba-106">no A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="0b8ba-107">fora Um ponteiro para o tamanho total de todas as alocações de memória.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b8ba-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0b8ba-108">Return Value</span></span>  
 <span data-ttu-id="0b8ba-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0b8ba-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b8ba-110">HRESULT</span></span>|<span data-ttu-id="0b8ba-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b8ba-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b8ba-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b8ba-112">S_OK</span></span>|<span data-ttu-id="0b8ba-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0b8ba-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="0b8ba-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="0b8ba-115">O domínio do aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="0b8ba-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b8ba-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b8ba-116">Remarks</span></span>  
 <span data-ttu-id="0b8ba-117">Esse método é o equivalente não gerenciado da propriedade gerenciada <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0b8ba-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8ba-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b8ba-118">Requirements</span></span>  
 <span data-ttu-id="0b8ba-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b8ba-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8ba-120">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0b8ba-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0b8ba-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b8ba-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b8ba-122">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8ba-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8ba-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="0b8ba-123">See also</span></span>

- [<span data-ttu-id="0b8ba-124">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="0b8ba-124">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="0b8ba-125">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b8ba-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="0b8ba-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="0b8ba-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0b8ba-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="0b8ba-127">Hosting</span></span>](index.md)
