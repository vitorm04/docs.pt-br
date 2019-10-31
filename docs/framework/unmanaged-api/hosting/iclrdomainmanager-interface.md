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
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129334"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="4bbf1-102">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="4bbf1-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="4bbf1-103">Permite que o host especifique o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar as propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="4bbf1-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bbf1-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4bbf1-104">Methods</span></span>  
  
|<span data-ttu-id="4bbf1-105">Método</span><span class="sxs-lookup"><span data-stu-id="4bbf1-105">Method</span></span>|<span data-ttu-id="4bbf1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bbf1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bbf1-107">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="4bbf1-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="4bbf1-108">Especifica o tipo, derivado da classe <xref:System.AppDomainManager?displayProperty=nameWithType>, do Gerenciador de domínio do aplicativo que será usado para inicializar o domínio do aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="4bbf1-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="4bbf1-109">Método SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="4bbf1-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="4bbf1-110">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="4bbf1-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bbf1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bbf1-111">Remarks</span></span>  
 <span data-ttu-id="4bbf1-112">Para obter uma instância dessa interface, chame o método [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) com o tipo de Gerenciador `IID_ICLRDomainManager`IID.</span><span class="sxs-lookup"><span data-stu-id="4bbf1-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bbf1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bbf1-113">Requirements</span></span>  
 <span data-ttu-id="4bbf1-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bbf1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bbf1-115">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4bbf1-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4bbf1-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bbf1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bbf1-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bbf1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbf1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bbf1-118">See also</span></span>

- [<span data-ttu-id="4bbf1-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="4bbf1-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4bbf1-120">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4bbf1-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
