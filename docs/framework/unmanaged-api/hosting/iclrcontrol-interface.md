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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06c1f4e1fcfe9c9c361a0e0bb2e8722577a13b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432889"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="e83f9-102">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e83f9-102">ICLRControl Interface</span></span>
<span data-ttu-id="e83f9-103">Fornece métodos que permitem obter referências a um host e configurem aspectos do, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e83f9-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e83f9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e83f9-104">Methods</span></span>  
  
|<span data-ttu-id="e83f9-105">Método</span><span class="sxs-lookup"><span data-stu-id="e83f9-105">Method</span></span>|<span data-ttu-id="e83f9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e83f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e83f9-107">Método GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="e83f9-108">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador, que o host pode usar para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="e83f9-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="e83f9-109">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="e83f9-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="e83f9-110">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e83f9-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e83f9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e83f9-111">Requirements</span></span>  
 <span data-ttu-id="e83f9-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83f9-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e83f9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e83f9-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e83f9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e83f9-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83f9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e83f9-116">See Also</span></span>  
 [<span data-ttu-id="e83f9-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="e83f9-118">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="e83f9-119">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="e83f9-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="e83f9-121">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="e83f9-122">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="e83f9-123">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="e83f9-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="e83f9-124">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="e83f9-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="e83f9-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="e83f9-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
