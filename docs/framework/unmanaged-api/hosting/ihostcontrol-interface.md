---
title: Interface IHostControl
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
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d0eaecef4cc34549c7d37953a5c8144bdd983692
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="e84fc-102">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="e84fc-102">IHostControl Interface</span></span>
<span data-ttu-id="e84fc-103">Fornece métodos para configurar o carregamento de assemblies e para determinar quais hospedagem interfaces com suporte no host.</span><span class="sxs-lookup"><span data-stu-id="e84fc-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e84fc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e84fc-104">Methods</span></span>  
  
|<span data-ttu-id="e84fc-105">Método</span><span class="sxs-lookup"><span data-stu-id="e84fc-105">Method</span></span>|<span data-ttu-id="e84fc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e84fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e84fc-107">Método GetHostManager</span><span class="sxs-lookup"><span data-stu-id="e84fc-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="e84fc-108">Obtém um ponteiro de interface para a implementação do host da interface com especificado `IID`.</span><span class="sxs-lookup"><span data-stu-id="e84fc-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="e84fc-109">Método SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="e84fc-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="e84fc-110">Notifica o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="e84fc-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e84fc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e84fc-111">Requirements</span></span>  
 <span data-ttu-id="e84fc-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e84fc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e84fc-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e84fc-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e84fc-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e84fc-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e84fc-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e84fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84fc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e84fc-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="e84fc-117">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e84fc-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="e84fc-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e84fc-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="e84fc-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e84fc-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
