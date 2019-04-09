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
ms.openlocfilehash: ce53149b92ca40ad50ecbefaf4701940e8567ae5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103916"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="1d447-102">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="1d447-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="1d447-103">Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="1d447-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d447-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1d447-104">Methods</span></span>  
  
|<span data-ttu-id="1d447-105">Método</span><span class="sxs-lookup"><span data-stu-id="1d447-105">Method</span></span>|<span data-ttu-id="1d447-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d447-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d447-107">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="1d447-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="1d447-108">Especifica o tipo, derivado de <xref:System.AppDomainManager?displayProperty=nameWithType> classe do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="1d447-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="1d447-109">Método SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="1d447-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="1d447-110">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="1d447-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d447-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d447-111">Remarks</span></span>  
 <span data-ttu-id="1d447-112">Para obter uma instância dessa interface, chame o [iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método com o tipo de Gerenciador IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="1d447-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d447-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d447-113">Requirements</span></span>  
 <span data-ttu-id="1d447-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d447-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d447-115">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1d447-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1d447-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1d447-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1d447-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1d447-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d447-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d447-118">See also</span></span>

- [<span data-ttu-id="1d447-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="1d447-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1d447-120">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="1d447-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
