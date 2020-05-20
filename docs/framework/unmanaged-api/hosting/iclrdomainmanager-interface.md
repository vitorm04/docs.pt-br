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
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615703"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="89ea4-102">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="89ea4-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="89ea4-103">Permite que o host especifique o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar as propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="89ea4-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89ea4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="89ea4-104">Methods</span></span>  
  
|<span data-ttu-id="89ea4-105">Método</span><span class="sxs-lookup"><span data-stu-id="89ea4-105">Method</span></span>|<span data-ttu-id="89ea4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="89ea4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89ea4-107">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="89ea4-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="89ea4-108">Especifica o tipo, derivado da <xref:System.AppDomainManager?displayProperty=nameWithType> classe, do Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="89ea4-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="89ea4-109">Método SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="89ea4-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="89ea4-110">Define as propriedades que serão usadas para inicializar o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="89ea4-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89ea4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="89ea4-111">Remarks</span></span>  
 <span data-ttu-id="89ea4-112">Para obter uma instância dessa interface, chame o método [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) com o tipo de Gerenciador IID `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="89ea4-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89ea4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89ea4-113">Requirements</span></span>  
 <span data-ttu-id="89ea4-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ea4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ea4-115">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="89ea4-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89ea4-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89ea4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89ea4-117">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ea4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ea4-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="89ea4-118">See also</span></span>

- [<span data-ttu-id="89ea4-119">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="89ea4-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="89ea4-120">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="89ea4-120">Hosting</span></span>](index.md)
