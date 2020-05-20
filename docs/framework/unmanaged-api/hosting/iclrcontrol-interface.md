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
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615826"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="70cd9-102">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="70cd9-102">ICLRControl Interface</span></span>
<span data-ttu-id="70cd9-103">Fornece métodos que permitem que um host obtenha referências e configure aspectos do, o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="70cd9-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70cd9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="70cd9-104">Methods</span></span>  
  
|<span data-ttu-id="70cd9-105">Método</span><span class="sxs-lookup"><span data-stu-id="70cd9-105">Method</span></span>|<span data-ttu-id="70cd9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="70cd9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70cd9-107">Método GetCLRManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="70cd9-108">Obtém um ponteiro de interface para uma instância de qualquer um dos tipos de Gerenciador que o host pode usar para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="70cd9-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="70cd9-109">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="70cd9-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="70cd9-110">Define um tipo derivado de <xref:System.AppDomainManager> como o tipo para gerenciadores de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70cd9-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70cd9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70cd9-111">Requirements</span></span>  
 <span data-ttu-id="70cd9-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cd9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cd9-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70cd9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70cd9-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70cd9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70cd9-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cd9-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="70cd9-116">See also</span></span>

- [<span data-ttu-id="70cd9-117">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="70cd9-118">Interface ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="70cd9-119">Interface ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="70cd9-120">Interface ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="70cd9-121">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="70cd9-122">Interface ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="70cd9-123">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="70cd9-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="70cd9-124">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="70cd9-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="70cd9-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="70cd9-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
