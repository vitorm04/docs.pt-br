---
title: Interface IHostControl
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 014e5c9951091046ae07374794743e82affcd5ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122259"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="9c33e-102">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="9c33e-102">IHostControl Interface</span></span>
<span data-ttu-id="9c33e-103">Fornece métodos para configurar o carregamento de assemblies e para determinar quais hospedando interfaces o oferece suporte ao host.</span><span class="sxs-lookup"><span data-stu-id="9c33e-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c33e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9c33e-104">Methods</span></span>  
  
|<span data-ttu-id="9c33e-105">Método</span><span class="sxs-lookup"><span data-stu-id="9c33e-105">Method</span></span>|<span data-ttu-id="9c33e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c33e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c33e-107">Método GetHostManager</span><span class="sxs-lookup"><span data-stu-id="9c33e-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="9c33e-108">Obtém um ponteiro de interface para a implementação do host da interface com especificado `IID`.</span><span class="sxs-lookup"><span data-stu-id="9c33e-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="9c33e-109">Método SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="9c33e-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="9c33e-110">Notifica o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="9c33e-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c33e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c33e-111">Requirements</span></span>  
 <span data-ttu-id="9c33e-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c33e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c33e-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c33e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c33e-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9c33e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9c33e-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9c33e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9c33e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c33e-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="9c33e-117">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9c33e-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="9c33e-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="9c33e-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9c33e-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9c33e-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
