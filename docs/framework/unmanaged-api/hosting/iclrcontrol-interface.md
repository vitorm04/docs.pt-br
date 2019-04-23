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
ms.openlocfilehash: f70e7958cc9ac198738ed72732fe7b6563c89067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175416"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="1ac4c-102">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="1ac4c-102">ICLRControl Interface</span></span>
<span data-ttu-id="1ac4c-103">Fornece métodos que permitem obter referências a um host e configurem aspectos do, o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1ac4c-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ac4c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1ac4c-104">Methods</span></span>  
  
|<span data-ttu-id="1ac4c-105">Método</span><span class="sxs-lookup"><span data-stu-id="1ac4c-105">Method</span></span>|<span data-ttu-id="1ac4c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ac4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ac4c-107">Método GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="1ac4c-108">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="1ac4c-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="1ac4c-109">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="1ac4c-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="1ac4c-110">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ac4c-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ac4c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ac4c-111">Requirements</span></span>  
 <span data-ttu-id="1ac4c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac4c-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ac4c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ac4c-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1ac4c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ac4c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ac4c-116">See also</span></span>

- [<span data-ttu-id="1ac4c-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1ac4c-118">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="1ac4c-119">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="1ac4c-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="1ac4c-121">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="1ac4c-122">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="1ac4c-123">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="1ac4c-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1ac4c-124">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="1ac4c-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="1ac4c-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="1ac4c-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
