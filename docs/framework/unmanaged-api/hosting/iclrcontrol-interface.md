---
title: Interface ICLRControl
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 914a2f6103fb0ffb9a7b9fcb895ecf0cd62f3c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126603"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="99959-102">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="99959-102">ICLRControl Interface</span></span>
<span data-ttu-id="99959-103">Fornece métodos que permitem que um host obtenha referências e configure aspectos do, o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="99959-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99959-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="99959-104">Methods</span></span>  
  
|<span data-ttu-id="99959-105">Método</span><span class="sxs-lookup"><span data-stu-id="99959-105">Method</span></span>|<span data-ttu-id="99959-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="99959-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99959-107">Método GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="99959-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="99959-108">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="99959-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="99959-109">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="99959-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="99959-110">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99959-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99959-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99959-111">Requirements</span></span>  
 <span data-ttu-id="99959-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99959-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99959-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99959-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99959-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99959-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99959-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99959-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99959-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99959-116">See also</span></span>

- [<span data-ttu-id="99959-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="99959-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="99959-118">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="99959-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="99959-119">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="99959-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="99959-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="99959-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="99959-121">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="99959-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="99959-122">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="99959-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="99959-123">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="99959-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="99959-124">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="99959-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="99959-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="99959-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
