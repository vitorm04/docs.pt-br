---
title: "Enumeração EInitializeNewDomainFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EInitializeNewDomainFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EInitializeNewDomainFlags
helpviewer_keywords: EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="31f02-102">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="31f02-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="31f02-103">Permite que o host fornecer o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="31f02-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31f02-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="31f02-105">Membros</span><span class="sxs-lookup"><span data-stu-id="31f02-105">Members</span></span>  
  
|<span data-ttu-id="31f02-106">Membro</span><span class="sxs-lookup"><span data-stu-id="31f02-106">Member</span></span>|<span data-ttu-id="31f02-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31f02-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="31f02-108">Sem sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="31f02-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="31f02-109">Informa o common language runtime (CLR) que o host não fará alterações para o estado de segurança do domínio do aplicativo no <xref:System.AppDomainManager.InitializeNewDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="31f02-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31f02-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="31f02-110">Remarks</span></span>  
 <span data-ttu-id="31f02-111">O [Iclrdomainmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) método usa um parâmetro do tipo `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="31f02-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f02-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31f02-112">Requirements</span></span>  
 <span data-ttu-id="31f02-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f02-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f02-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31f02-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31f02-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31f02-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31f02-116">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f02-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f02-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31f02-117">See Also</span></span>  
 [<span data-ttu-id="31f02-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="31f02-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="31f02-119">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="31f02-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
