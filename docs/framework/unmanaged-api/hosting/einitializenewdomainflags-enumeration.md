---
title: Enumeração EInitializeNewDomainFlags
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d69b12404459de5dbc1c7748deee6ca09c1e5182
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772419"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="5238f-102">Enumeração EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="5238f-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="5238f-103">Permite que o host fornecer o tempo de execução com informações sobre a inicialização de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5238f-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5238f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5238f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="5238f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5238f-105">Members</span></span>  
  
|<span data-ttu-id="5238f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5238f-106">Member</span></span>|<span data-ttu-id="5238f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5238f-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="5238f-108">Sem sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="5238f-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="5238f-109">Informa o common language runtime (CLR) que o host não fará alterações para o estado de segurança do domínio do aplicativo na <xref:System.AppDomainManager.InitializeNewDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5238f-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5238f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5238f-110">Remarks</span></span>  
 <span data-ttu-id="5238f-111">O [iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) método utiliza um parâmetro de tipo `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="5238f-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5238f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5238f-112">Requirements</span></span>  
 <span data-ttu-id="5238f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5238f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5238f-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5238f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5238f-115">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5238f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5238f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5238f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5238f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5238f-117">See also</span></span>

- [<span data-ttu-id="5238f-118">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5238f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="5238f-119">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="5238f-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
