---
title: Interface ICLRDomainManager
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436352"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="9ad3d-102">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="9ad3d-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="9ad3d-103">Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ad3d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9ad3d-104">Methods</span></span>  
  
|<span data-ttu-id="9ad3d-105">Método</span><span class="sxs-lookup"><span data-stu-id="9ad3d-105">Method</span></span>|<span data-ttu-id="9ad3d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ad3d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ad3d-107">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="9ad3d-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="9ad3d-108">Especifica o tipo derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="9ad3d-109">Método SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="9ad3d-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="9ad3d-110">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ad3d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ad3d-111">Remarks</span></span>  
 <span data-ttu-id="9ad3d-112">Para obter uma instância desta interface, chame o [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método com o tipo de Gerenciador IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="9ad3d-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad3d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ad3d-113">Requirements</span></span>  
 <span data-ttu-id="9ad3d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad3d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad3d-115">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9ad3d-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ad3d-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9ad3d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ad3d-117">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad3d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad3d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ad3d-118">See Also</span></span>  
 [<span data-ttu-id="9ad3d-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="9ad3d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9ad3d-120">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9ad3d-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
