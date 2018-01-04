---
title: Interface ICLRControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93d87107e1a69b0a047dbf156124fe49cd95d16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="b6f78-102">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b6f78-102">ICLRControl Interface</span></span>
<span data-ttu-id="b6f78-103">Fornece métodos que permitem obter referências a um host e configurem aspectos do, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b6f78-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6f78-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b6f78-104">Methods</span></span>  
  
|<span data-ttu-id="b6f78-105">Método</span><span class="sxs-lookup"><span data-stu-id="b6f78-105">Method</span></span>|<span data-ttu-id="b6f78-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6f78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6f78-107">Método GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="b6f78-108">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador, que o host pode usar para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="b6f78-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="b6f78-109">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="b6f78-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="b6f78-110">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6f78-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6f78-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6f78-111">Requirements</span></span>  
 <span data-ttu-id="b6f78-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f78-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f78-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6f78-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6f78-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b6f78-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6f78-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f78-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6f78-116">See Also</span></span>  
 [<span data-ttu-id="b6f78-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b6f78-118">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="b6f78-119">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="b6f78-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="b6f78-121">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="b6f78-122">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="b6f78-123">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="b6f78-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="b6f78-124">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="b6f78-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="b6f78-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b6f78-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
